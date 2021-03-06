---
ms.openlocfilehash: ab7731d34aad5b6b6481f13ba11b778393e2cac2
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858458"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup.DynamicBase n’est plus aléatoire en activant UseRandomizedStringHashAlgorithm

|   |   |
|---|---|
|Détails|Avant .NET Framework 4.6, la valeur de <xref:System.AppDomainSetup.DynamicBase> était aléatoire entre les domaines d’application, ou entre les processus, si UseRandomizedStringHashAlgorithm était activé dans le fichier de configuration de l’application. À compter de .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> retourne un résultat stable entre différentes instances d’une application en cours d’exécution et entre différents domaines d’application. Les bases dynamiques seront toujours différentes pour différentes applications ; cette modification supprime uniquement l’élément de nommage aléatoire pour différentes instances de la même application.|
|Suggestion|Gardez à l’esprit que l’activation de <code>UseRandomizedStringHashAlgorithm</code> ne rendra pas <xref:System.AppDomainSetup.DynamicBase> aléatoire. Si une base aléatoire est nécessaire, elle doit être générée dans le code de votre application plutôt que via cette API.|
|Portée|Microsoft Edge|
|Version|4.6|
|Type|Runtime|
|API affectées|<ul><li><xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|

