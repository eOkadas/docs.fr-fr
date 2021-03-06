---
title: Moderniser le cycle de vie de votre application avec les pipelines d’intégration continue/de déploiement continu et les outils DevOps dans le cloud
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Moderniser le cycle de vie de votre application avec des pipelines CI/CD et des outils DevOps dans le Cloud
ms.date: 04/30/2018
ms.openlocfilehash: 4e4436ac4a622a82cc990b977b03eeae95ca9368
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181906"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Moderniser le cycle de vie de votre application avec les pipelines d’intégration continue/de déploiement continu et les outils DevOps dans le cloud

Aujourd’hui, les entreprises doivent innover à un rythme rapide pour être compétitifs dans la place de marché. La mise en place d’applications modernes de haute qualité requiert des outils et processus DevOps essentiels pour mettre en œuvre ce cycle constant d’innovation. Avec les outils DevOps appropriés, les développeurs peuvent simplifier le déploiement continu et obtenir des applications innovantes plus rapidement pour les mains des utilisateurs.

Bien que les pratiques d’intégration et de déploiement continues soient bien établies, l’introduction des conteneurs introduit de nouvelles considérations, en particulier lorsque vous travaillez avec des applications à plusieurs conteneurs.

Azure DevOps Services prend en charge l’intégration et le déploiement continus d’applications à plusieurs conteneurs dans divers environnements via les tâches officielles de déploiement Azure DevOps Services :

- [Déployer sur un Web App pour conteneurs Azure](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [Déployer dans le service Azure Kubernetes](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

Toutefois, vous pouvez également effectuer le déploiement sur un [essaimeur](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) ou DC/OS à l’aide de Azure DevOps services des tâches basées sur des scripts.

Pour faciliter le déploiement, ces outils offrent une excellente expérience de déploiement de développement à la production pour les charges de travail de conteneur, avec un choix de solutions de développement et d’intégration continue/de déploiement continu.

La figure 4-12 illustre un pipeline de déploiement continu qui se déploie sur un cluster Kubernetes dans Azure Container Service.

![Azure DevOps Services pipeline de déploiement continu, déploiement sur un cluster Kubernetes](./media/image12.png)

**Figure 4-12.** Azure DevOps Services pipeline de déploiement continu, déploiement sur un cluster Kubernetes

>[!div class="step-by-step"]
>[Précédent](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Suivant](migrate-to-hybrid-cloud-scenarios.md)
