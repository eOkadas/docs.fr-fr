---
title: services de streaming gRPC et champs répétés-gRPC pour les développeurs WCF
description: Comparaison entre les champs répétés et les services de streaming pour passer des collections de données avec gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7dc3c8f5bf2efc304da7d50661ba47db500e67a0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184070"
---
# <a name="grpc-streaming-services-versus-repeated-fields"></a>services de streaming gRPC et champs répétés

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

les services gRPC offrent deux moyens de retourner des jeux de données ou des listes d’objets. La spécification de message de mémoires tampons `repeated` de protocole utilise le mot clé pour déclarer des listes ou des tableaux de messages dans un autre message. La spécification du service gRPC utilise `stream` le mot clé pour déclarer une connexion permanente longue sur laquelle plusieurs messages sont envoyés et peut être traitée individuellement. La `stream` fonctionnalité peut également être utilisée pour des données temporelles de longue durée, telles que des notifications ou des messages de journal, mais ce chapitre prend en compte son utilisation pour retourner un jeu de données unique.

Ce que vous devez utiliser dépend de divers facteurs, tels que la taille globale du jeu de données, le temps nécessaire pour créer le jeu de données à la fin du client ou du serveur, et si l’utilisateur du DataSet peut commencer à agir dessus dès que le premier élément est disponible , ou a besoin du jeu de données complet pour faire quelque chose d’utile.

## <a name="when-to-use-repeated-fields"></a>Quand utiliser `repeated` des champs

Pour tout jeu de données limité en taille et pouvant être généré dans son intégralité dans un laps de temps donné (par exemple, sous une seconde), vous devez utiliser `repeated` un champ dans un message Protobuf normal. Par exemple, dans un système de commerce électronique, la création d’une liste d’éléments dans une commande est probablement rapide et la liste n’est pas très volumineuse. Le retour d’un seul message `repeated` avec un champ est un ordre de grandeur plus rapide `stream` que l’utilisation d’un et entraîne moins de surcharge du réseau.

Si le client a besoin de toutes les données avant de commencer à le traiter et que le jeu de données est suffisamment petit pour être construit `repeated` en mémoire, envisagez d’utiliser un champ même si la création réelle du jeu de données en mémoire sur le serveur est plus lente.

## <a name="when-to-use-stream-methods"></a>Quand utiliser `stream` des méthodes

Les jeux de données où les objets de message sont potentiellement très volumineux sont transférés le mieux à l’aide de demandes de streaming ou de réponses. Il est plus efficace de construire un objet volumineux en mémoire, de l’écrire sur le réseau, puis de libérer les ressources. Cette approche permet d’améliorer l’évolutivité de votre service.

De même, les jeux de données de taille non contrainte doivent être envoyés sur des flux pour éviter de manquer de mémoire lors de la construction de ces derniers.

Pour les jeux de données où chaque élément individuel peut être traité séparément par le consommateur, vous devez envisager d’utiliser un flux si cela signifie que la progression peut être indiquée à l’utilisateur final. Cela pourrait améliorer la réactivité apparente d’une application, même si elle doit être équilibrée par rapport aux performances globales de l’application.

Un autre scénario dans lequel les flux peuvent être utiles est l’endroit où un message est traité sur plusieurs services. Si chaque service d’une chaîne retourne un flux, le service Terminal (autrement dit, le dernier de la chaîne) peut commencer à retourner des messages qui peuvent être traités et retransmis le long de la chaîne au demandeur d’origine, qui peut soit retourner un flux, soit agréger le résultats dans un message de réponse unique. Cette approche se prête bien à des modèles tels que Map/Reduce.

>[!div class="step-by-step"]
>[Précédent](migrate-duplex-services.md)
>[Suivant](client-libraries.md)
