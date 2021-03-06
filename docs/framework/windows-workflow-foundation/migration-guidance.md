---
title: Conseils de migration
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 45f81b29f63701f690e396de2e9834f9933fd775
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796805"
---
# <a name="migration-guidance"></a>Conseils de migration
Dans le [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], Microsoft publie la deuxième version principale de Windows Workflow Foundation (WF). [!INCLUDE[wf1](../../../includes/wf1-md.md)]a été publié dans WinFX (cela comprenait les types dans System. Workflow\* . Namespaces; désormais connu sous le nom de WF3) [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]et amélioré dans. WF3 fait également partie du [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], mais il existe avec la nouvelle technologie de workflow (les types dans System. Activities.\* Namespaces, appelés WF4). Lorsque vous pensez au moment opportun d'adopter WF4, il est important de savoir tout d'abord que c'est vous qui décidez.  
  
- WF3 est une partie complètement prise en charge de [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
- Les applications WF3 sont exécutées sur [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] sans modification et continuent à être totalement prises en charge.  
  
- De nouvelles applications WF3 peuvent être créées et vos applications existantes peuvent être modifiées dans Visual Studio 2012 et sont entièrement prises en charge.  
  
 Par conséquent, la décision d’adopter le .NET Framework 4 est dissociée de votre décision de passer à WF4 (System. Activities\*.) à partir de WF3 (System\*. Workflow.). Cette rubrique fournit des liens vers des conseils de migration WF qui fournissent des informations sur l'utilisation de WF3 et WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>Livres blancs et livres de recettes sur la migration WF (en anglais)  
 La rubrique [vue d’ensemble de la migration WF](https://go.microsoft.com/fwlink/?LinkId=153873) fournit une vue d’ensemble de la relation entre WF3 et WF4 et les stratégies de migration. Les rubriques d'accompagnement traitent de sujets spécifiques.  
  
 [Vue d’ensemble de la migration WF](https://go.microsoft.com/fwlink/?LinkId=153873)  
 Décrit la relation entre WF3 et WF4 ainsi que les choix dont vous disposez en tant qu'utilisateur ou qu'utilisateur potentiel de la technologie de workflow dans .NET 4.  
  
 [Migration de WF: Meilleures pratiques pour le développement de WF3](https://go.microsoft.com/fwlink/?LinkId=153852)  
 Explique comment concevoir des artefacts WF3 afin que leur migration vers WF4 soit plus facile.  
  
 [Aide de WF: Matière](https://go.microsoft.com/fwlink/?LinkId=153854)  
 Explique comment reporter des investissements liés aux règles dans des solutions [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
 [Aide de WF: Machine à États](https://go.microsoft.com/fwlink/?LinkId=153855)  
 Explique la modélisation des flux de contrôle WF4 en l'absence d'une activité Ordinateur-État.  
  
 Notez que ces conseils s'appliquent uniquement aux projets de workflow qui ciblent le .NET Framework 4. Les workflows de machine à états ont été ajoutés dans le .NET 4.0.1 avec la mise en production de la mise à jour 1 de la plateforme, et ont été inclus dans le .NET Framework 4.5. Pour plus d’informations sur les workflows d’ordinateur d’État dans .NET 4.0.1-4.0.3 et .NET Framework 4,5, consultez [mise à jour d' 4.0.1 pour les fonctionnalités de Microsoft .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) et [flux de travail d’ordinateur d’État](state-machine-workflows.md).  
  
 [Livre de recettes sur la migration WF: Activités personnalisées](https://go.microsoft.com/fwlink/?LinkId=153856)  
 Fournit des exemples et des instructions pour une nouvelle conception des activités personnalisées WF3 sur WF4.  
  
 [Livre de recettes sur la migration WF: Activités personnalisées avancées](https://go.microsoft.com/fwlink/?LinkId=275560)  
 Explique comment reconcevoir des activités personnalisées WF3 avancées qui utilisent les files d'attente WF3 et planifier des activités enfants en tant qu'activités personnalisées WF4.  
  
 [Livre de recettes sur la migration WF: Workflows](https://go.microsoft.com/fwlink/?LinkId=153858)  
 Fournit des exemples et des instructions pour une nouvelle conception des workflows WF3 sur WF4.  
  
 [Livre de recettes sur la migration WF: Hébergement de workflow](https://go.microsoft.com/fwlink/?LinkId=275561)  
 Explique comment reconcevoir code d'hébergement WF3 en tant que code d'hébergement WF4. L'objectif est de couvrir les principales différences de l'hébergement de workflow entre WF3 et WF4.  
  
 [Livre de recettes sur la migration WF: Suivi de workflow](https://go.microsoft.com/fwlink/?LinkId=275562)  
 Explique comment reconcevoir le code et la configuration de suivi WF3 à l'aide du code et de la configuration de suivi équivalents WF4.  
  
 [Aide de WF: Services de workflow](https://go.microsoft.com/fwlink/?LinkId=275564)  
 Fournit des instructions détaillées orientées exemple pour reconcevoir les workflows qui implémentent des services Web Windows Communication Foundation (WCF) (en général connus sous le nom de services de workflowl) créés dans WF3 de façon à utiliser WF4, pour les scénarios courants d'activités prédéfinies.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.Statements.Interop>
