---
title: API de prise en charge de l'hébergement de navigateur WPF natif
ms.date: 03/30/2017
f1_keywords:
- AutoGeneratedOrientationPage
helpviewer_keywords:
- browser hosting support [WPF]
- WPF browser hosting support APIs [WPF]
ms.assetid: 82c133a8-d760-45fb-a2b9-3a997537f1d4
ms.openlocfilehash: 29ff388685c67d06d7c5866a46954d5ade72acb1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053362"
---
# <a name="native-wpf-browser-hosting-support-apis"></a>API de prise en charge de l'hébergement de navigateur WPF natif
L’hébergement [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] d’applications dans des navigateurs Web est facilité par un serveur de documents actifs (également connu sous le nom de DocObject) inscrit à partir de l’hôte WPF. Internet Explorer peut s’activer et s’intégrer directement à un document actif. Pour l’hébergement d’applications XBAP et de documents XAML libre dans les [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] navigateurs Mozilla, fournit un plug-in NPAPI, qui fournit [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] un environnement d’hébergement similaire au serveur de documents actifs comme le fait Internet Explorer. Toutefois, la méthode la plus simple pour héberger des applications XBAP et des documents XAML dans d’autres navigateurs et applications autonomes consiste à utiliser le contrôle de navigateur Web Internet Explorer. Le contrôle de navigateur Web fournit l’environnement d’hébergement de serveur de documents actifs complexe, mais il permet à son propre hôte de personnaliser et d’étendre cet environnement et de communiquer directement avec l’objet de document actif actuel.  
  
 Le [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] serveur de documents actif implémente plusieurs interfaces d’hébergement courantes, notamment [IOleObject](https://go.microsoft.com/fwlink/?LinkId=162049), [IOleDocument](https://go.microsoft.com/fwlink/?LinkId=162050), [IOleInPlaceActiveObject](https://go.microsoft.com/fwlink/?LinkId=162051), [IPersistMoniker](https://go.microsoft.com/fwlink/?LinkId=162045), [IOleCommandTarget](https://go.microsoft.com/fwlink/?LinkId=162047). Lorsqu’ils sont hébergés dans le contrôle de navigateur Web, ces interfaces peuvent être des requêtes de l’objet retourné par la propriété [IWebBrowser2 ::D ver](https://go.microsoft.com/fwlink/?LinkId=162048) .  
  
## <a name="iolecommandtarget"></a>IOleCommandTarget  
 L’implémentation d' [IOleCommandTarget](https://go.microsoft.com/fwlink/?LinkId=162047) dans WPF active document Server prend en charge de nombreuses commandes de navigation et propres aux navigateurs du groupe de commandes OLE standard (avec un GUID de groupe de commandes null). En outre, il reconnaît un groupe de commandes personnalisé appelé CGID_PresentationHost. Actuellement, une seule commande est définie dans ce groupe.  
  
```cpp  
DEFINE_GUID(CGID_PresentationHost, 0xd0288c55, 0xd6, 0x4f5e, 0xa8, 0x51, 0x79, 0xde, 0xc5, 0x1b, 0x10, 0xec);  
enum PresentationHostCommands {   
   PHCMDID_TABINTO = 1   
};  
```  
  
 PHCMDID_TABINTO indique à PresentationHost de basculer le focus sur le premier ou le dernier élément pouvant être actif dans son contenu, en fonction de l’état de la touche Maj.  
  
## <a name="in-this-section"></a>Dans cette section  
 [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md)  
 [IWpfHostSupport](iwpfhostsupport.md)
