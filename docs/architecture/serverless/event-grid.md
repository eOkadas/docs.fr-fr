---
title: Applications sans serveur Azure Event Grid
description: Azure Event Grid est une solution sans serveur pour la remise d’événements fiable et le routage à grande échelle sur un modèle de paiement à l’événement.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4970130ede0c96c645129ee6c8c7d54cb1114042
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577572"
---
# <a name="event-grid"></a><span data-ttu-id="c1bb5-103">Event Grid</span><span class="sxs-lookup"><span data-stu-id="c1bb5-103">Event Grid</span></span>

<span data-ttu-id="c1bb5-104">[Azure Event Grid](/azure/event-grid/overview) fournit une infrastructure sans serveur pour les applications basées sur les événements.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-104">[Azure Event Grid](/azure/event-grid/overview) provides serverless infrastructure for event-based applications.</span></span> <span data-ttu-id="c1bb5-105">Vous pouvez publier sur Event Grid à partir de n’importe quelle source et utiliser des messages de n’importe quelle plateforme.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-105">You can publish to Event Grid from any source and consume messages from any platform.</span></span> <span data-ttu-id="c1bb5-106">Event Grid offre également une prise en charge intégrée des événements des ressources Azure pour simplifier l’intégration avec vos applications.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-106">Event Grid also has built-in support for events from Azure resources to streamline integration with your applications.</span></span> <span data-ttu-id="c1bb5-107">Par exemple, vous pouvez vous abonner à des événements de stockage d’objets BLOB pour notifier votre application quand un fichier est chargé.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-107">For example, you can subscribe to blob storage events to notify your app when a file is uploaded.</span></span> <span data-ttu-id="c1bb5-108">Votre application peut ensuite publier un message de grille d’événements personnalisé qui est consommé par d’autres applications Cloud ou locales.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-108">Your application can then publish a custom event grid message that is consumed by other cloud or on-premises applications.</span></span> <span data-ttu-id="c1bb5-109">Event Grid a été conçu pour gérer de manière fiable une grande échelle.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-109">Event Grid was built to reliably handle massive scale.</span></span> <span data-ttu-id="c1bb5-110">Vous bénéficiez des avantages de la publication et de l’abonnement aux messages sans la surcharge liée à la configuration de l’infrastructure nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-110">You get the benefits of publishing and subscribing to messages without the overhead of setting up the necessary infrastructure.</span></span>

![Logo Event Grid](./media/event-grid-logo.png)

<span data-ttu-id="c1bb5-112">Les principales fonctionnalités d’Event Grid sont les suivantes:</span><span class="sxs-lookup"><span data-stu-id="c1bb5-112">The major features of event grid include:</span></span>

* <span data-ttu-id="c1bb5-113">Routage d’événements entièrement géré.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-113">Fully managed event routing.</span></span>
* <span data-ttu-id="c1bb5-114">Livraison d’événements presque en temps réel à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-114">Near real-time event delivery at scale.</span></span>
* <span data-ttu-id="c1bb5-115">Couverture étendue à l’intérieur et à l’extérieur d’Azure.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-115">Broad coverage both inside and outside of Azure.</span></span>

## <a name="scenarios"></a><span data-ttu-id="c1bb5-116">Scénarios</span><span class="sxs-lookup"><span data-stu-id="c1bb5-116">Scenarios</span></span>

<span data-ttu-id="c1bb5-117">Event Grid résout plusieurs scénarios différents.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-117">Event Grid addresses several different scenarios.</span></span> <span data-ttu-id="c1bb5-118">Cette section couvre les trois des plus courants.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-118">This section covers three of the most common ones.</span></span>

### <a name="ops-automation"></a><span data-ttu-id="c1bb5-119">Automatisation des opérations</span><span class="sxs-lookup"><span data-stu-id="c1bb5-119">Ops automation</span></span>

![Automatisation des opérations](./media/ops-automation.png)

<span data-ttu-id="c1bb5-121">Event Grid pouvez accélérer l’automatisation et simplifier l’application des stratégies en avertissant [Azure Automation](https://docs.microsoft.com/azure/automation) quand l’infrastructure est approvisionnée.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-121">Event Grid can help speed automation and simplify policy enforcement by notifying [Azure Automation](https://docs.microsoft.com/azure/automation) when infrastructure is provisioned.</span></span>

### <a name="application-integration"></a><span data-ttu-id="c1bb5-122">Intégration d’applications</span><span class="sxs-lookup"><span data-stu-id="c1bb5-122">Application integration</span></span>

![Intégration d’applications](./media/app-integration.png)

<span data-ttu-id="c1bb5-124">Vous pouvez utiliser Event Grid pour connecter votre application à d’autres services.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-124">You can use Event Grid to connect your app to other services.</span></span> <span data-ttu-id="c1bb5-125">À l’aide des protocoles HTTP standard, même les applications héritées peuvent être facilement modifiées pour publier des messages Event Grid.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-125">Using standard HTTP protocols, even legacy apps can be easily modified to publish Event Grid messages.</span></span> <span data-ttu-id="c1bb5-126">Des webhooks sont disponibles pour d’autres services et plateformes pour utiliser des messages Event Grid.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-126">Web hooks are available for other services and platforms to consume Event Grid messages.</span></span>

### <a name="serverless-apps"></a><span data-ttu-id="c1bb5-127">Applications sans serveur</span><span class="sxs-lookup"><span data-stu-id="c1bb5-127">Serverless apps</span></span>

![Applications sans serveur](./media/serverless-apps.png)

<span data-ttu-id="c1bb5-129">Event Grid pouvez déclencher Azure Functions, Logic Apps ou votre propre code personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-129">Event Grid can trigger Azure Functions, Logic Apps, or your own custom code.</span></span> <span data-ttu-id="c1bb5-130">L’un des principaux avantages de l’utilisation de Event Grid est qu’elle utilise un mécanisme *Push* pour envoyer des messages lorsque des événements se produisent.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-130">A major benefit of using Event Grid is that it uses a *push* mechanism to send messages when events occur.</span></span> <span data-ttu-id="c1bb5-131">L’architecture Push consomme moins de ressources et évolue mieux que les mécanismes d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-131">The push architecture consumes fewer resources and scales better than *polling* mechanisms.</span></span> <span data-ttu-id="c1bb5-132">L’interrogation doit vérifier les mises à jour à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-132">Polling must check for updates on a regular interval.</span></span>

## <a name="event-grid-vs-other-azure-messaging-services"></a><span data-ttu-id="c1bb5-133">Event Grid et d’autres services de messagerie Azure</span><span class="sxs-lookup"><span data-stu-id="c1bb5-133">Event Grid vs. other Azure messaging services</span></span>

<span data-ttu-id="c1bb5-134">Azure fournit plusieurs services de messagerie, y compris [Event hubs](https://docs.microsoft.com/azure/event-hubs) et [service bus](https://docs.microsoft.com/azure/service-bus-messaging).</span><span class="sxs-lookup"><span data-stu-id="c1bb5-134">Azure provides several messaging services, including [Event Hubs](https://docs.microsoft.com/azure/event-hubs) and [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging).</span></span> <span data-ttu-id="c1bb5-135">Chaque est conçu pour répondre à un ensemble spécifique de cas d’usage.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-135">Each is designed to address a specific set of use cases.</span></span> <span data-ttu-id="c1bb5-136">Le diagramme suivant fournit une vue d’ensemble des différences entre les services.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-136">The following diagram provides a high-level overview of the differences between the services.</span></span>

![Comparaison de la messagerie Azure](./media/azure-messaging-services.png)

<span data-ttu-id="c1bb5-138">Pour une comparaison plus détaillée, consultez comparer les [services de messagerie](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).</span><span class="sxs-lookup"><span data-stu-id="c1bb5-138">For a more in-depth comparison, see [Compare messaging services](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).</span></span>

## <a name="performance-targets"></a><span data-ttu-id="c1bb5-139">Cibles de performances</span><span class="sxs-lookup"><span data-stu-id="c1bb5-139">Performance targets</span></span>

<span data-ttu-id="c1bb5-140">À l’aide de Event Grid vous pouvez tirer parti des garanties de performances suivantes:</span><span class="sxs-lookup"><span data-stu-id="c1bb5-140">Using Event Grid you can take advantage of the following performance guarantees:</span></span>

* <span data-ttu-id="c1bb5-141">Latence de bout en bout sous-seconde dans le 99e centile.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-141">Subsecond end-to-end latency in the 99th percentile.</span></span>
* <span data-ttu-id="c1bb5-142">disponibilité de 99,99%.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-142">99.99% availability.</span></span>
* <span data-ttu-id="c1bb5-143">10 millions événements par seconde par région.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-143">10 million events per second per region.</span></span>
* <span data-ttu-id="c1bb5-144">100 millions abonnements par région.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-144">100 million subscriptions per region.</span></span>
* <span data-ttu-id="c1bb5-145">50-latence MS Publisher.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-145">50-ms publisher latency.</span></span>
* <span data-ttu-id="c1bb5-146">nouvelle tentative de 24 heures avec interruption exponentielle pour la livraison garantie dans la fenêtre de 1 jour.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-146">24-hour retry with exponential back-off for guaranteed delivery in the 1-day window.</span></span>
* <span data-ttu-id="c1bb5-147">Basculement régional transparent.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-147">Transparent regional failover.</span></span>

## <a name="event-grid-schema"></a><span data-ttu-id="c1bb5-148">Schéma Event Grid</span><span class="sxs-lookup"><span data-stu-id="c1bb5-148">Event Grid schema</span></span>

<span data-ttu-id="c1bb5-149">Event Grid utilise un schéma standard pour encapsuler les événements personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-149">Event Grid uses a standard schema to wrap custom events.</span></span> <span data-ttu-id="c1bb5-150">Le schéma est comme une enveloppe qui encapsule votre élément de données personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-150">The schema is like an envelope that wraps your custom data element.</span></span> <span data-ttu-id="c1bb5-151">Voici un exemple Event Grid message:</span><span class="sxs-lookup"><span data-stu-id="c1bb5-151">Here is an example Event Grid message:</span></span>

```json
[{
    "id": "03e24f21-a955-43cc-8921-1f61a6081ce0",
    "eventType": "myCustomEvent",
    "subject": "foo/bar/12",
    "eventTime": "2018-09-22T10:36:01+00:00",
    "data": {
        "favoriteColor": "blue",
        "favoriteAnimal": "panther",
        "favoritePlanet": "Jupiter"
    },
    "dataVersion": "1.0"
}]
```

<span data-ttu-id="c1bb5-152">Tout ce qui concerne le message est standard `data` , à l’exception de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-152">Everything about the message is standard except the `data` property.</span></span> <span data-ttu-id="c1bb5-153">Vous pouvez inspecter le message et utiliser `eventType` et `dataVersion` pour désérialiser la partie personnalisée de la charge utile.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-153">You can inspect the message and use the `eventType` and `dataVersion` to de-serialize the custom portion of the payload.</span></span>

## <a name="azure-resources"></a><span data-ttu-id="c1bb5-154">Ressources Azure</span><span class="sxs-lookup"><span data-stu-id="c1bb5-154">Azure resources</span></span>

<span data-ttu-id="c1bb5-155">L’un des principaux avantages de l’utilisation de Event Grid est l’automatisation des messages générés par Azure.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-155">A major benefit of using Event Grid is the automatic messages produced by Azure.</span></span> <span data-ttu-id="c1bb5-156">Dans Azure, les ressources publient automatiquement sur une *rubrique* qui vous permet de vous abonner à différents événements.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-156">In Azure, resources automatically publish to a *topic* that allows you to subscribe for various events.</span></span> <span data-ttu-id="c1bb5-157">Le tableau suivant répertorie les types de ressources, les types de messages et les événements qui sont disponibles automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-157">The following table lists the resource types, message types, and events that are available automatically.</span></span>

| <span data-ttu-id="c1bb5-158">Ressource Azure</span><span class="sxs-lookup"><span data-stu-id="c1bb5-158">Azure resource</span></span> | <span data-ttu-id="c1bb5-159">Type d'événement</span><span class="sxs-lookup"><span data-stu-id="c1bb5-159">Event type</span></span> | <span data-ttu-id="c1bb5-160">Description</span><span class="sxs-lookup"><span data-stu-id="c1bb5-160">Description</span></span> |
| -------------- | ---------- | ----------- |
| <span data-ttu-id="c1bb5-161">Abonnement Azure</span><span class="sxs-lookup"><span data-stu-id="c1bb5-161">Azure subscription</span></span> | <span data-ttu-id="c1bb5-162">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="c1bb5-162">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="c1bb5-163">Déclenché lorsqu’une opération de création ou de mise à jour de ressource est réussie.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-163">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="c1bb5-164">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="c1bb5-164">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="c1bb5-165">Déclenché lorsqu’une opération de création ou de mise à jour de ressource échoue.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-165">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="c1bb5-166">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="c1bb5-166">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="c1bb5-167">Déclenché lorsqu’une opération de création ou de mise à jour de ressource est annulée.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-167">Raised when a resource create or update operation is canceled.</span></span> |
|  | <span data-ttu-id="c1bb5-168">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="c1bb5-168">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="c1bb5-169">Déclenché lorsqu’une opération de suppression de ressource est réussie.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-169">Raised when a resource delete operation succeeds.</span></span> |
|  | <span data-ttu-id="c1bb5-170">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="c1bb5-170">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="c1bb5-171">Déclenché en cas d’échec d’une opération de suppression de ressource.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-171">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="c1bb5-172">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="c1bb5-172">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="c1bb5-173">Déclenché lorsqu’une opération de suppression de ressource est annulée.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-173">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="c1bb5-174">Cet événement se produit lorsque le déploiement d’un modèle est annulé.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-174">This event happens when a template deployment is canceled.</span></span> |
| <span data-ttu-id="c1bb5-175">Stockage d'objets blob</span><span class="sxs-lookup"><span data-stu-id="c1bb5-175">Blob storage</span></span> | <span data-ttu-id="c1bb5-176">Microsoft.Storage.BlobCreated</span><span class="sxs-lookup"><span data-stu-id="c1bb5-176">Microsoft.Storage.BlobCreated</span></span> | <span data-ttu-id="c1bb5-177">Déclenché lorsqu’un objet blob est créé.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-177">Raised when a blob is created.</span></span> |
| | <span data-ttu-id="c1bb5-178">Microsoft.Storage.BlobDeleted</span><span class="sxs-lookup"><span data-stu-id="c1bb5-178">Microsoft.Storage.BlobDeleted</span></span> | <span data-ttu-id="c1bb5-179">Déclenché lorsqu’un objet blob est supprimé.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-179">Raised when a blob is deleted.</span></span> |
| <span data-ttu-id="c1bb5-180">Hubs d’événements</span><span class="sxs-lookup"><span data-stu-id="c1bb5-180">Event hubs</span></span> | <span data-ttu-id="c1bb5-181">Microsoft.EventHub.CaptureFileCreated</span><span class="sxs-lookup"><span data-stu-id="c1bb5-181">Microsoft.EventHub.CaptureFileCreated</span></span> | <span data-ttu-id="c1bb5-182">Déclenché lors de la création d’un fichier de capture.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-182">Raised when a capture file is created.</span></span>
| <span data-ttu-id="c1bb5-183">IoT Hub</span><span class="sxs-lookup"><span data-stu-id="c1bb5-183">IoT Hub</span></span> | <span data-ttu-id="c1bb5-184">Microsoft.Devices.DeviceCreated</span><span class="sxs-lookup"><span data-stu-id="c1bb5-184">Microsoft.Devices.DeviceCreated</span></span> | <span data-ttu-id="c1bb5-185">Publié quand un appareil est inscrit auprès d’un hub IoT.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-185">Published when a device is registered to an IoT hub.</span></span> |
| | <span data-ttu-id="c1bb5-186">Microsoft.Devices.DeviceDeleted</span><span class="sxs-lookup"><span data-stu-id="c1bb5-186">Microsoft.Devices.DeviceDeleted</span></span> | <span data-ttu-id="c1bb5-187">Publié quand un appareil est supprimé d’un hub IoT.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-187">Published when a device is deleted from an IoT hub.</span></span> |
| <span data-ttu-id="c1bb5-188">Groupes de ressources</span><span class="sxs-lookup"><span data-stu-id="c1bb5-188">Resource groups</span></span> | <span data-ttu-id="c1bb5-189">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="c1bb5-189">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="c1bb5-190">Déclenché lorsqu’une opération de création ou de mise à jour de ressource est réussie.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-190">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="c1bb5-191">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="c1bb5-191">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="c1bb5-192">Déclenché lorsqu’une opération de création ou de mise à jour de ressource échoue.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-192">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="c1bb5-193">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="c1bb5-193">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="c1bb5-194">Déclenché lorsqu’une opération de création ou de mise à jour de ressource est annulée.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-194">Raised when a resource create or update operation is canceled.</span></span> |
| | <span data-ttu-id="c1bb5-195">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="c1bb5-195">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="c1bb5-196">Déclenché lorsqu’une opération de suppression de ressource est réussie.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-196">Raised when a resource delete operation succeeds.</span></span> |
| | <span data-ttu-id="c1bb5-197">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="c1bb5-197">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="c1bb5-198">Déclenché en cas d’échec d’une opération de suppression de ressource.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-198">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="c1bb5-199">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="c1bb5-199">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="c1bb5-200">Déclenché lorsqu’une opération de suppression de ressource est annulée.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-200">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="c1bb5-201">Cet événement se produit lorsque le déploiement d’un modèle est annulé.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-201">This event happens when a template deployment is canceled.</span></span> |

<span data-ttu-id="c1bb5-202">Pour plus d’informations, consultez [Azure Event Grid le schéma d’événement](https://docs.microsoft.com/azure/event-grid/event-schema).</span><span class="sxs-lookup"><span data-stu-id="c1bb5-202">For more information, see [Azure Event Grid event schema](https://docs.microsoft.com/azure/event-grid/event-schema).</span></span>

<span data-ttu-id="c1bb5-203">Vous pouvez accéder à Event Grid à partir de n’importe quel type d’application, même s’il s’exécute en local.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-203">You can access Event Grid from any type of application, even one that runs on-premises.</span></span>

## <a name="conclusion"></a><span data-ttu-id="c1bb5-204">Conclusion</span><span class="sxs-lookup"><span data-stu-id="c1bb5-204">Conclusion</span></span>

<span data-ttu-id="c1bb5-205">Dans ce chapitre, vous avez découvert la plateforme sans serveur Azure composée de Azure Functions, Logic Apps et Event Grid.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-205">In this chapter you learned about the Azure serverless platform that is composed of Azure Functions, Logic Apps, and Event Grid.</span></span> <span data-ttu-id="c1bb5-206">Vous pouvez utiliser ces ressources pour créer une architecture d’application entièrement sans serveur, ou créer une solution hybride qui interagit avec d’autres ressources Cloud et serveurs locaux.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-206">You can use these resources to build an entirely serverless app architecture, or create a hybrid solution that interacts with other cloud resources and on-premises servers.</span></span> <span data-ttu-id="c1bb5-207">Combiné à une plateforme de données sans serveur telle qu' [Azure SQL](https://docs.microsoft.com/azure/sql-database) ou [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), vous pouvez créer des applications Cloud natives entièrement gérées.</span><span class="sxs-lookup"><span data-stu-id="c1bb5-207">Combined with a serverless data platform such as [Azure SQL](https://docs.microsoft.com/azure/sql-database) or [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), you can build fully managed cloud native applications.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="c1bb5-208">Ressources recommandées</span><span class="sxs-lookup"><span data-stu-id="c1bb5-208">Recommended resources</span></span>

* [<span data-ttu-id="c1bb5-209">Plans App service</span><span class="sxs-lookup"><span data-stu-id="c1bb5-209">App service plans</span></span>](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
* [<span data-ttu-id="c1bb5-210">Application Insights</span><span class="sxs-lookup"><span data-stu-id="c1bb5-210">Application Insights</span></span>](https://docs.microsoft.com/azure/application-insights)
* [<span data-ttu-id="c1bb5-211">Application Insights Analytics</span><span class="sxs-lookup"><span data-stu-id="c1bb5-211">Application Insights Analytics</span></span>](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
* [<span data-ttu-id="c1bb5-212">Bleu Mettez votre application dans le Cloud avec Azure Functions sans serveur</span><span class="sxs-lookup"><span data-stu-id="c1bb5-212">Azure: Bring your app to the cloud with serverless Azure Functions</span></span>](https://channel9.msdn.com/events/Connect/2017/E102)
* [<span data-ttu-id="c1bb5-213">Azure Event Grid</span><span class="sxs-lookup"><span data-stu-id="c1bb5-213">Azure Event Grid</span></span>](https://docs.microsoft.com/azure/event-grid/overview)
* [<span data-ttu-id="c1bb5-214">Schéma d’événement Azure Event Grid</span><span class="sxs-lookup"><span data-stu-id="c1bb5-214">Azure Event Grid event schema</span></span>](https://docs.microsoft.com/azure/event-grid/event-schema)
* [<span data-ttu-id="c1bb5-215">Event Hubs Azure</span><span class="sxs-lookup"><span data-stu-id="c1bb5-215">Azure Event Hubs</span></span>](https://docs.microsoft.com/azure/event-hubs)
* [<span data-ttu-id="c1bb5-216">Documentation Azure Functions</span><span class="sxs-lookup"><span data-stu-id="c1bb5-216">Azure Functions documentation</span></span>](https://docs.microsoft.com/azure/azure-functions)
* [<span data-ttu-id="c1bb5-217">Concepts relatifs aux déclencheurs et aux liaisons Azure Functions</span><span class="sxs-lookup"><span data-stu-id="c1bb5-217">Azure Functions triggers and bindings concepts</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
* [<span data-ttu-id="c1bb5-218">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="c1bb5-218">Azure Logic Apps</span></span>](https://docs.microsoft.com/azure/logic-apps)
* [<span data-ttu-id="c1bb5-219">Azure Service Bus</span><span class="sxs-lookup"><span data-stu-id="c1bb5-219">Azure Service Bus</span></span>](https://docs.microsoft.com/azure/service-bus-messaging)
* [<span data-ttu-id="c1bb5-220">Stockage table Azure</span><span class="sxs-lookup"><span data-stu-id="c1bb5-220">Azure Table Storage</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
* [<span data-ttu-id="c1bb5-221">Comparer les fonctions 1. x et 2. x</span><span class="sxs-lookup"><span data-stu-id="c1bb5-221">Compare functions 1.x and 2.x</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-versions)
* [<span data-ttu-id="c1bb5-222">Connexion à des sources de données locales avec la passerelle de données locale Azure</span><span class="sxs-lookup"><span data-stu-id="c1bb5-222">Connecting to on-premises data sources with Azure On-premises Data Gateway</span></span>](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
* [<span data-ttu-id="c1bb5-223">Créez votre première fonction dans le Portail Azure</span><span class="sxs-lookup"><span data-stu-id="c1bb5-223">Create your first function in the Azure portal</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
* [<span data-ttu-id="c1bb5-224">Créez votre première fonction à l’aide de l’Azure CLI</span><span class="sxs-lookup"><span data-stu-id="c1bb5-224">Create your first function using the Azure CLI</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
* [<span data-ttu-id="c1bb5-225">Créer votre première fonction à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c1bb5-225">Create your first function using Visual Studio</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
* [<span data-ttu-id="c1bb5-226">Fonctions prises en charge par les fonctions</span><span class="sxs-lookup"><span data-stu-id="c1bb5-226">Functions supported languages</span></span>](https://docs.microsoft.com/azure/azure-functions/supported-languages)
* [<span data-ttu-id="c1bb5-227">Analyser Azure Functions</span><span class="sxs-lookup"><span data-stu-id="c1bb5-227">Monitor Azure Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
* [<span data-ttu-id="c1bb5-228">Utiliser des Azure Functions Proxies</span><span class="sxs-lookup"><span data-stu-id="c1bb5-228">Work with Azure Functions Proxies</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
><span data-ttu-id="c1bb5-229">[Précédent](logic-apps.md)
>[Suivant](durable-azure-functions.md)</span><span class="sxs-lookup"><span data-stu-id="c1bb5-229">[Previous](logic-apps.md)
[Next](durable-azure-functions.md)</span></span>