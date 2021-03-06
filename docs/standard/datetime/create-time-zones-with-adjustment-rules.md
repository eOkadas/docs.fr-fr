---
title: 'Procédure : créer des fuseaux horaires avec des règles d’ajustement'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], creating
- time zones [.NET Framework], and adjustment rules
- adjustment rule [.NET Framework]
ms.assetid: c52ef192-13a9-435f-8015-3b12eae8c47c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ae739d3c5dd233c2129950666846979edfba370
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106672"
---
# <a name="how-to-create-time-zones-with-adjustment-rules"></a>Procédure : créer des fuseaux horaires avec des règles d’ajustement

Les informations de fuseau horaire précises requises par une application peuvent ne pas être présentes sur un système particulier pour plusieurs raisons:

- Le fuseau horaire n’a jamais été défini dans le Registre du système local.

- Les données relatives au fuseau horaire ont été modifiées ou supprimées du Registre.

- Le fuseau horaire ne contient pas d’informations exactes sur les ajustements de fuseau horaire pour une période historique particulière.

Dans ce cas, vous pouvez appeler la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode pour définir le fuseau horaire requis par votre application. Vous pouvez utiliser les surcharges de cette méthode pour créer un fuseau horaire avec ou sans règles d’ajustement. Si le fuseau horaire prend en charge l’heure d’été, vous pouvez définir des ajustements à l’aide de règles d’ajustement fixes ou flottantes. (Pour obtenir les définitions de ces termes, consultez la section «Terminologie relative aux fuseaux horaires» dans [vue d’ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md).)

> [!IMPORTANT]
> Les fuseaux horaires personnalisés créés en <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> appelant la méthode ne sont pas ajoutés au registre. Au lieu de cela, ils sont accessibles uniquement par le biais de la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> référence d’objet retournée par l’appel de méthode.

Cette rubrique montre comment créer un fuseau horaire avec des règles d’ajustement. Pour créer un fuseau horaire qui ne prend pas en charge les règles d’ajustement à [l’heure d’été, consultez Procédure: Créer des fuseaux horaires sans](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)règles d’ajustement.

### <a name="to-create-a-time-zone-with-floating-adjustment-rules"></a>Pour créer un fuseau horaire avec des règles d’ajustement flottantes

1. Pour chaque ajustement (c’est-à-dire, pour chaque transition en dehors et vers l’heure standard sur un intervalle de temps donné), procédez comme suit:

    1. Définissez l’heure de début de la transition pour le réglage du fuseau horaire.

       Vous devez appeler la <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> méthode et lui passer une <xref:System.DateTime> valeur qui définit l’heure de la transition, une valeur entière qui définit le mois de la transition, une valeur entière qui définit la semaine où la transition se produit et un <xref:System.DayOfWeek> valeur qui définit le jour de la semaine où la transition se produit. Cet appel de méthode instancie <xref:System.TimeZoneInfo.TransitionTime> un objet.

    2. Définissez l’heure de fin de la transition pour le réglage du fuseau horaire. Cela nécessite un autre appel à <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A?displayProperty=nameWithType> la méthode. Cet appel de méthode instancie un <xref:System.TimeZoneInfo.TransitionTime> deuxième objet.

    3. Appelez la <xref:System.TimeZoneInfo.AdjustmentRule.CreateAdjustmentRule%2A> méthode et passez-lui les dates de début et de fin effectives de <xref:System.TimeSpan> l’ajustement, un objet qui définit la durée de la transition et les <xref:System.TimeZoneInfo.TransitionTime> deux objets qui définissent le moment où les transitions vers et depuis l’heure d’été l’heure se produit. Cet appel de méthode instancie <xref:System.TimeZoneInfo.AdjustmentRule> un objet.

    4. Assignez l' <xref:System.TimeZoneInfo.AdjustmentRule> objet à un <xref:System.TimeZoneInfo.AdjustmentRule> tableau d’objets.

2. Définissez le nom d’affichage du fuseau horaire. Le nom d’affichage suit un format relativement standard dans lequel le décalage du fuseau horaire par rapport au temps universel coordonné (UTC, Universal Time Coordinated) est placé entre parenthèses et est suivi d’une chaîne qui identifie le fuseau horaire, une ou plusieurs des villes du fuseau horaire, ou un ou plusieurs cou les critures ou les régions dans le fuseau horaire.

3. Définissez le nom de l’heure d’hiver du fuseau horaire. En règle générale, cette chaîne est également utilisée comme identificateur du fuseau horaire.

4. Définissez le nom de l’heure d’été du fuseau horaire.

5. Si vous souhaitez utiliser un identificateur différent du nom standard du fuseau horaire, définissez l’identificateur de fuseau horaire.

6. Instanciez <xref:System.TimeSpan> un objet qui définit le décalage du fuseau horaire par rapport à l’heure UTC. Les fuseaux horaires dont les heures sont postérieures à l’heure UTC ont un décalage positif. Les fuseaux horaires dont les heures sont antérieures à l’heure UTC ont un décalage négatif.

7. Appelez la <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> méthode pour instancier le nouveau fuseau horaire.

## <a name="example"></a>Exemple

L’exemple suivant définit un fuseau horaire central pour le États-Unis qui comprend des règles d’ajustement pour divers intervalles de temps de 1918 à la présente.

[!code-csharp[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#5)]
[!code-vb[System.TimeZone2.CreateTimeZone#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#5)]

Le fuseau horaire créé dans cet exemple a plusieurs règles d’ajustement. Vous devez veiller à ce que les dates de début et de fin effectives de toute règle d’ajustement ne chevauchent pas les dates d’une autre règle d’ajustement. En cas de chevauchement, une <xref:System.InvalidTimeZoneException> exception est levée.

Pour les règles d’ajustement flottantes, la valeur 5 est `week` passée au paramètre <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> de la méthode pour indiquer que la transition se produit à la dernière semaine d’un mois donné.

Lors de la création du <xref:System.TimeZoneInfo.AdjustmentRule> tableau d’objets à utiliser <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%2CSystem.String%2CSystem.TimeZoneInfo.AdjustmentRule%5B%5D%29?displayProperty=nameWithType> dans l’appel de méthode, le code peut initialiser le tableau à la taille requise par le nombre d’ajustements à créer pour le fuseau horaire. Au lieu de cela, cet exemple <xref:System.Collections.Generic.List%601.Add%2A> de code appelle la méthode pour ajouter chaque règle <xref:System.Collections.Generic.List%601> d’ajustement <xref:System.TimeZoneInfo.AdjustmentRule> à une collection générique d’objets. Le code appelle ensuite la <xref:System.Collections.Generic.List%601.CopyTo%2A> méthode pour copier les membres de cette collection dans le tableau.

L’exemple utilise également la <xref:System.TimeZoneInfo.TransitionTime.CreateFixedDateRule%2A> méthode pour définir des ajustements de date fixe. Cela est similaire à l’appel <xref:System.TimeZoneInfo.TransitionTime.CreateFloatingDateRule%2A> de la méthode, sauf qu’elle nécessite uniquement l’heure, le mois et le jour des paramètres de transition.

L’exemple peut être testé à l’aide d’un code tel que le suivant:

[!code-csharp[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#7)]
[!code-vb[System.TimeZone2.CreateTimeZone#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#7)]

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Que les espaces de noms suivants soient importés:

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Vue d’ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md)
- [Guide pratique pour Créer des fuseaux horaires sans règles d’ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
