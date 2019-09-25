---
title: Annexe-gRPC pour les développeurs WCF
description: Présentation des transactions distribuées et de leur implémentation dans les architectures de microservices modernes.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 10c4e77794c5ffe1aa6d5a629ce0b6cdf92f4ada
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184616"
---
# <a name="appendix-a---transactions"></a><span data-ttu-id="90ae8-103">Annexe A-transactions</span><span class="sxs-lookup"><span data-stu-id="90ae8-103">Appendix A - Transactions</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="90ae8-104">Les transactions distribuées prises en charge par Windows Communication Foundation (WCF) permettent d’effectuer des opérations atomiques sur plusieurs services.</span><span class="sxs-lookup"><span data-stu-id="90ae8-104">Windows Communication Foundation (WCF) supported distributed transactions, allowing atomic operations to be performed across multiple services.</span></span> <span data-ttu-id="90ae8-105">Cette fonctionnalité était basée sur le [Distributed Transaction Coordinator Microsoft](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="90ae8-105">This functionality was based on the [Microsoft Distributed Transaction Coordinator](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85)).</span></span>

<span data-ttu-id="90ae8-106">Dans le paysage des microservices moderne, ce type de traitement automatisé des transactions distribuées n’est pas possible.</span><span class="sxs-lookup"><span data-stu-id="90ae8-106">In the modern microservices landscape, this type of automated distributed transaction processing isn't possible.</span></span> <span data-ttu-id="90ae8-107">Il existe un trop grand nombre de technologies différentes, notamment les bases de données relationnelles, les magasins de données NoSQL et les systèmes de messagerie, sans oublier la combinaison de systèmes d’exploitation, de langages de programmation et d’infrastructures qui peuvent être utilisés dans un environnement unique.</span><span class="sxs-lookup"><span data-stu-id="90ae8-107">There are too many different technologies at play, including relational databases, NoSQL data stores, and messaging systems, not to mention the mix of operating systems, programming languages and frameworks that may be used in a single environment.</span></span>

<span data-ttu-id="90ae8-108">La transaction distribuée WCF est une implémentation de ce qu’on appelle une [validation en deux phases (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol).</span><span class="sxs-lookup"><span data-stu-id="90ae8-108">The WCF distributed transaction is an implementation of what is known as a [two-phase commit (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol).</span></span> <span data-ttu-id="90ae8-109">Il est possible d’implémenter des transactions 2PC manuellement en coordonnant les messages entre les services, en créant des transactions ouvertes au sein de chaque service et en envoyant des messages « Commit » ou « Rollback » en fonction de la réussite ou de l’échec.</span><span class="sxs-lookup"><span data-stu-id="90ae8-109">It's possible to implement 2PC transactions manually by coordinating messages across services, creating open transactions within each service and sending "commit" or "rollback" messages depending upon success or failure.</span></span> <span data-ttu-id="90ae8-110">Toutefois, la complexité impliquée dans la gestion de 2PC peut augmenter de façon exponentielle à mesure que les systèmes évoluent, et les transactions ouvertes contiennent des verrous de base de données qui peuvent avoir un impact négatif sur les performances ou, pire, provoquent des blocages interservices.</span><span class="sxs-lookup"><span data-stu-id="90ae8-110">However, the complexity that is involved in managing 2PC can increase exponentially as systems evolve, and open transactions hold database locks that can negatively impact performance or, worse, cause cross-service deadlocks.</span></span>

<span data-ttu-id="90ae8-111">Si possible, il est préférable d’éviter totalement les transactions distribuées.</span><span class="sxs-lookup"><span data-stu-id="90ae8-111">If possible, it's best to avoid distributed transactions altogether.</span></span> <span data-ttu-id="90ae8-112">Si deux éléments de données sont liés comme pour exiger des mises à jour atomiques, envisagez de les gérer à la fois avec le même service et en appliquant ces modifications atomiques à l’aide d’une requête ou d’un message unique à ce service.</span><span class="sxs-lookup"><span data-stu-id="90ae8-112">If two items of data are so linked as to require atomic updates, consider handling them both with the same service, and applying those atomic changes using a single request or message to that service.</span></span>

<span data-ttu-id="90ae8-113">Si ce n’est pas possible, une alternative consiste à utiliser le [modèle saga](https://microservices.io/patterns/data/saga.html).</span><span class="sxs-lookup"><span data-stu-id="90ae8-113">If that isn't possible, then one alternative is to use the [Saga pattern](https://microservices.io/patterns/data/saga.html).</span></span> <span data-ttu-id="90ae8-114">Dans un saga, les mises à jour sont traitées de manière séquentielle. à mesure que chaque mise à jour est réussie, le suivant est déclenché.</span><span class="sxs-lookup"><span data-stu-id="90ae8-114">In a saga, updates are processing sequentially; as each update succeeds the next one is triggered.</span></span> <span data-ttu-id="90ae8-115">Ces déclencheurs peuvent être propagés du service au service, ou gérés par un coordinateur saga ou « Orchestrator ».</span><span class="sxs-lookup"><span data-stu-id="90ae8-115">These triggers can be propagated from service to service, or managed by a saga coordinator or "orchestrator".</span></span> <span data-ttu-id="90ae8-116">Si une mise à jour échoue à tout moment pendant le processus, les services qui ont déjà effectué leurs mises à jour appliquent une logique spécifique pour les inverser.</span><span class="sxs-lookup"><span data-stu-id="90ae8-116">If an update fails at any point during the process, the services that have already completed their updates apply specific logic to reverse them.</span></span>

<span data-ttu-id="90ae8-117">Une autre option consiste à utiliser la conception pilotée par domaine (DDD) et la séparation des responsabilités de commande/requête (CQRS), comme décrit dans le [livre électronique sur les microservices .net](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/).</span><span class="sxs-lookup"><span data-stu-id="90ae8-117">Another option is to use Domain Driven Design (DDD) and Command/Query Responsibility Segregation (CQRS), as described in the [.NET Microservices e-book](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/).</span></span> <span data-ttu-id="90ae8-118">En particulier, l’utilisation d’événements de domaine ou d’une [source d’événements](https://martinfowler.com/eaaDev/EventSourcing.html) peut aider à garantir&mdash;que les mises à jour sont cohérentes si elles ne sont pas appliquées immédiatement.&mdash;</span><span class="sxs-lookup"><span data-stu-id="90ae8-118">In particular, using domain events or [event sourcing](https://martinfowler.com/eaaDev/EventSourcing.html) can help to ensure that updates are consistently&mdash;if not immediately&mdash;applied.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="90ae8-119">Précédent</span><span class="sxs-lookup"><span data-stu-id="90ae8-119">Previous</span></span>](application-performance-management.md)