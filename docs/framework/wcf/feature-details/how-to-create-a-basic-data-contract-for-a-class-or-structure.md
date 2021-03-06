---
title: 'Procédure : créer un contrat de données de base pour une classe ou structure'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 15c59f3ee7cbefafef7a304cfd1477685fff68f2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968460"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Procédure : créer un contrat de données de base pour une classe ou structure
Cette rubrique illustre les étapes de base pour créer un contrat de données à l'aide d'une classe ou d'une structure. Pour plus d’informations sur les contrats de données et leur utilisation, consultez [utilisation de contrats de données](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Pour obtenir un didacticiel qui vous guide tout au long des étapes de création d’un client et d’un service de base Windows Communication Foundation (WCF), consultez le [didacticiel prise en main](../../../../docs/framework/wcf/getting-started-tutorial.md). Pour obtenir un exemple d’application fonctionnel qui se compose d’un service et d’un client de base, consultez [contrat de données de base](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Pour créer un contrat de données de base destiné à une classe ou une structure  
  
1. Déclarez que le type a un contrat de données en appliquant l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> à la classe. Notez que tous les types publics, y compris ceux sans attributs, sont sérialisables. Le <xref:System.Runtime.Serialization.DataContractSerializer> déduit un contrat de données si l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> est absent. Pour plus d’informations, consultez [types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2. Définissez les membres (propriétés, champs ou événements) sérialisés en appliquant l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à chaque membre. Ces membres sont appelés des membres de données. Par défaut, tous les types publics sont sérialisables. Pour plus d’informations, consultez [types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    > Vous pouvez appliquer l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> aux champs privés, ce qui expose les données aux autres. Vérifiez que le membre ne contient pas de données sensibles.  
  
## <a name="example"></a>Exemples  
 L'exemple suivant montre comment créer un contrat de données pour le type `Person` en appliquant les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> à la classe et à ses membres.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Utilisation de contrats de données](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Didacticiel Bien démarrer](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [Prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md)
