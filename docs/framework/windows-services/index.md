---
title: Développement des applications de service Windows
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
ms.openlocfilehash: 61f969c22ac06bd6ed20ccfa9124db3bb35d0692
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053543"
---
# <a name="develop-windows-service-apps"></a>Développer des applications de service Windows

Utilisez Visual Studio ou le SDK .NET Framework pour créer facilement des services. En fait, vous créez une application qui est installée comme service. Ce type d’application est appelé un service Windows. Grâce aux fonctionnalités du framework, vous pouvez non seulement créer des services, les installer, les démarrer et les arrêter, mais aussi contrôler leur comportement.

> [!NOTE]
> Dans Visual Studio, vous pouvez créer un service dans le code managé en Visual C# ou Visual Basic, qui peut interagir avec le code C++ existant, si nécessaire. Ou, vous pouvez créer un service Windows en C++ natif à l’aide de [l’Assistant Projet ATL](/cpp/atl/reference/atl-project-wizard).

## <a name="in-this-section"></a>Dans cette section

[Introduction aux applications de service Windows](introduction-to-windows-service-applications.md)

Fournit une vue d’ensemble des applications de service Windows, de la durée de vie d’un service, et des différences entre les applications de service et les autres types de projets courants.

[Procédure pas à pas : Création d’une application de service Windows dans le Concepteur de composants](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

Fournit un exemple de création d’un service en Visual Basic et Visual C#.

[Architecture de programmation d’une application de service](service-application-programming-architecture.md)

Explique les éléments de langage utilisés dans la programmation d’un service.

[Guide pratique pour créer des services Windows](how-to-create-windows-services.md)

Décrit le processus de création et de configuration de services Windows à l’aide du modèle de projet de service Windows.

## <a name="related-sections"></a>Rubriques connexes

<xref:System.ServiceProcess.ServiceBase> - Décrit les principales fonctionnalités de la classe <xref:System.ServiceProcess.ServiceBase> qui est utilisée pour créer des services.

<xref:System.ServiceProcess.ServiceProcessInstaller> - Décrit les fonctionnalités de la classe <xref:System.ServiceProcess.ServiceProcessInstaller>. Celle-ci, utilisée avec la classe <xref:System.ServiceProcess.ServiceInstaller>, permet d’installer et de désinstaller vos services.

<xref:System.ServiceProcess.ServiceInstaller> - Décrit les fonctionnalités de la classe <xref:System.ServiceProcess.ServiceInstaller>. Celle-ci, utilisée avec la classe <xref:System.ServiceProcess.ServiceProcessInstaller>, permet d’installer et de désinstaller votre service.

[Créer des projets à partir de modèles](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) - Décrit les types de projets utilisés dans ce chapitre et comment faire votre choix.
