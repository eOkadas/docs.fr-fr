---
title: 'Procédure : créer des fuseaux horaires sans règles d’ajustement'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 510112c8b19ec002d1dcf918eb983b55dee68fd0
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106670"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>Procédure : créer des fuseaux horaires sans règles d’ajustement

Les informations de fuseau horaire précises requises par une application peuvent ne pas être présentes sur un système particulier pour plusieurs raisons:

- Le fuseau horaire n’a jamais été défini dans le Registre du système local.

- Les données relatives au fuseau horaire ont été modifiées ou supprimées du Registre.

- Le fuseau horaire existe mais il ne contient pas d’informations exactes sur les ajustements de fuseau horaire pour une période historique particulière.

Dans ce cas, vous pouvez appeler la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode pour définir le fuseau horaire requis par votre application. Vous pouvez utiliser les surcharges de cette méthode pour créer un fuseau horaire avec ou sans règles d’ajustement. Si le fuseau horaire prend en charge l’heure d’été, vous pouvez définir des ajustements à l’aide de règles d’ajustement fixes ou flottantes. (Pour obtenir les définitions de ces termes, consultez la section «Terminologie relative aux fuseaux horaires» dans [vue d’ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Les fuseaux horaires personnalisés créés en <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> appelant la méthode ne sont pas ajoutés au registre. Au lieu de cela, ils sont accessibles uniquement par le biais de la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> référence d’objet retournée par l’appel de méthode.

Cette rubrique montre comment créer un fuseau horaire sans règle d’ajustement. Pour créer un fuseau horaire qui prend en charge les règles d’ajustement à [l’heure d’été, consultez Procédure: Créer des fuseaux horaires avec](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)des règles d’ajustement.

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>Pour créer un fuseau horaire sans règles d’ajustement

1. Définissez le nom d’affichage du fuseau horaire.

   Le nom d’affichage suit un format relativement standard dans lequel le décalage du fuseau horaire par rapport au temps universel coordonné (UTC, Universal Time Coordinated) est placé entre parenthèses et est suivi d’une chaîne qui identifie le fuseau horaire, une ou plusieurs des villes du fuseau horaire, ou un ou plusieurs cou les critures ou les régions dans le fuseau horaire.

2. Définissez le nom de l’heure d’hiver du fuseau horaire. En règle générale, cette chaîne est également utilisée comme identificateur du fuseau horaire.

3. Si vous souhaitez utiliser un identificateur différent du nom standard du fuseau horaire, définissez l’identificateur de fuseau horaire.

4. Instanciez <xref:System.TimeSpan> un objet qui définit le décalage du fuseau horaire par rapport à l’heure UTC. Les fuseaux horaires dont les heures sont postérieures à l’heure UTC ont un décalage positif. Les fuseaux horaires dont les heures sont antérieures à l’heure UTC ont un décalage négatif.

5. Appelez la <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> méthode pour instancier le nouveau fuseau horaire.

## <a name="example"></a>Exemple

L’exemple suivant définit un fuseau horaire personnalisé pour Mawson, Antarctique, qui n’a aucune règle d’ajustement.

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

La chaîne assignée <xref:System.TimeZoneInfo.DisplayName%2A> à la propriété suit un format standard dans lequel le décalage du fuseau horaire par rapport à l’heure UTC est suivi d’une description conviviale du fuseau horaire.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Que les espaces de noms suivants soient importés:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Vue d’ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md)
- [Guide pratique : Créer des fuseaux horaires avec des règles d’ajustement](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
