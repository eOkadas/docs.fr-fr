---
title: 'Procédure : Personnaliser les flux avec le fournisseur de réflexion (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: 43f46729ba84356bcb6507779bef9e4fd35bc315
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790676"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Procédure : Personnaliser les flux avec le fournisseur de réflexion (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet de personnaliser la sérialisation Atom dans une réponse du service de données pour pouvoir mapper les propriétés d'une entité aux éléments inutilisés définis dans le protocole AtomPub. Cette rubrique indique comment définir des attributs de mappage pour les types d'entité dans un modèle de données défini à l'aide du fournisseur de réflexion. Pour plus d’informations, consultez [Personnalisation des flux](feed-customization-wcf-data-services.md).  
  
 Le modèle de données de cet exemple est défini dans la [rubrique Procédure : Créer un service de données à l’aide du fournisseur de réflexion](create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>Exemples  
 Dans l'exemple suivant, les deux propriétés du type `Order` sont mappées aux éléments Atom existants. La propriété `Product` du type `Item` est mappée à un attribut de flux personnalisé dans un espace de noms séparé.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Exemple  
 L'exemple précédent retourne le résultat suivant pour l'URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseur de réflexion](reflection-provider-wcf-data-services.md)
