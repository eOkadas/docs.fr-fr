---
title: Détails relatifs à l'implémentation du protocole WCF Data Services
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 1cd4204d9e1626ac45bccf3954fdaf1c156af7f8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779654"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Détails relatifs à l'implémentation du protocole WCF Data Services
## <a name="odata-protocol-implementation-details"></a>Détails de l'implémentation du protocole OData  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] requiert qu'un service de données qui implémente le protocole fournisse un ensemble minimum spécifique de fonctionnalités. Ces fonctionnalités sont décrites dans les documents de protocole en termes de « doit » et « doit ». D’autres fonctionnalités facultatives sont décrites en termes de « mai ». Cette rubrique décrit ces fonctionnalités facultatives qui ne sont pas actuellement implémentées par [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Pour plus d’informations, consultez [la documentation sur le protocole OData](https://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Prise en charge de l'option de requête $format  
 Le protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prend en charge les flux JavaScript Notation (JSON) et Atom, et [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fournit l'option de requête système `$format` pour permettre à un client de demander le format du flux de réponse. Cette option de requête du système (si prise en charge par le service de données) doit substituer la valeur de l'en-tête Accept de la requête. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] prend en charge le retour de flux JSON et Atom. Toutefois, l'implémentation par défaut ne prend pas en charge l'option de requête `$format` et utilise uniquement la valeur de l'en-tête Accept pour déterminer le format de la réponse. Il y a des cas où votre service de données doit prendre en charge l'option de requête `$format`, par exemple lorsque les clients ne peuvent pas définir l'en-tête Accept. Pour prendre en charge ces scénarios, vous devez étendre votre service de données pour gérer cette option dans l'URI. Vous pouvez ajouter cette fonctionnalité à votre service de données en [téléchargeant la prise en charge de JSONP et de format contrôlé par URL pour ADO.NET Data Services](https://go.microsoft.com/fwlink/?LinkId=208228) exemple de projet à partir du site Web MSDN Code Gallery et en l’ajoutant à votre projet de service de données. Cet exemple supprime l'option de requête `$format` et remplace l'en-tête Accept par `application/json`. Lorsque vous incluez l'exemple de projet et ajoutez `JSONPSupportBehaviorAttribute` à votre classe de service de données, le service peut gérer l'option de requête `$format``$format=json`. Une personnalisation plus poussée de cet exemple de projet est requise pour gérer également `$format=atom` ou d'autres formats personnalisés.  
  
## <a name="wcf-data-services-behaviors"></a>Comportements des services de données WCF  
 Les comportements suivants [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ne sont pas explicitement définis par le protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] :  
  
### <a name="default-sorting-behavior"></a>Comportement de tri par défaut  
 Lorsqu'une demande de requête envoyée au service de données inclut une option de requête système `$top` ou `$skip` et n'inclut pas d'option de requête système `$orderby`, le flux retourné est trié par les propriétés de clé, dans l'ordre croissant. Cela est dû au fait que le dimensionnement est requis pour garantir la pagination correcte des résultats. Pour cela, le service de données ajoute une expression de classement à la requête. Ce comportement se produit également lorsque la pagination orientée serveur est vérifiée dans le service de données. Pour plus d’informations, consultez [configuration du service de données](configuring-the-data-service-wcf-data-services.md). Pour contrôler l’ordre du flux retourné, vous devez inclure `$orderby` dans l’URI de la requête.  
  
## <a name="see-also"></a>Voir aussi

- [Définition de WCF Data Services](defining-wcf-data-services.md)
- [Bibliothèque cliente WCF Data Services](wcf-data-services-client-library.md)
