---
title: Mémoires tampons de protocole-gRPC pour les développeurs WCF
description: Présentation du format de câble des mémoires tampons de protocole utilisé pour la mise en réseau gRPC.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 4f9031c86731ea7ded4a812be9967237e52c4b39
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184168"
---
# <a name="protocol-buffers"></a>Mémoires tampons de protocole

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

les services gRPC envoient et reçoivent des données sous forme de *messages de tampon de protocole (Protobuf)* , similaires aux contrats de données de WCF. Protobuf est un moyen efficace de sérialiser des données structurées pour que les ordinateurs puissent les lire et les écrire, sans la surcharge que les formats explicites, tels que XML ou JSON, impliquent.

Ce chapitre explique comment fonctionne Protobuf et comment définir vos propres messages Protobuf.

## <a name="how-protobuf-works"></a>Fonctionnement de Protobuf

La plupart des techniques de sérialisation d’objets .NET, y compris les contrats de données WCF, fonctionnent à l’aide de la réflexion pour analyser la structure d’objets au moment de l’exécution. En revanche, la plupart des bibliothèques Protobuf nécessitent que vous définissiez la structure en amont à l’aide d’un langage dédié ( `.proto` langue de la*mémoire tampon du protocole*) dans un fichier. Ce fichier est ensuite utilisé par un compilateur pour générer du code pour l’une des plateformes prises en charge, y compris .NETC++, Java, C/, JavaScript et bien plus encore. Le compilateur Protobuf, `protoc`, est géré par Google, bien que d’autres implémentations soient disponibles. Le code généré est efficace et optimisé pour la sérialisation et la désérialisation rapides des données.

Le format de câble Protobuf lui-même est un encodage binaire, qui utilise des astuces astucieuses pour réduire le nombre d’octets utilisés pour représenter les messages. La connaissance du format d’encodage binaire n’est pas nécessaire pour utiliser Protobuf, mais si vous êtes intéressé, vous pouvez en savoir plus à ce sujet sur [le site Web de mémoires tampons de protocole](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Précédent](why-grpc.md)
>[Suivant](protobuf-messages.md)
