---
title: Workflow de développement de la boucle interne pour les applications Docker
description: Découvrez le workflow de type « boucle interne » pour le développement des applications Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 04e1b29e6a0cef89df05cc9124806c74a38b5249
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214354"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Workflow de développement de la boucle interne pour les applications Docker

Avant de déclencher le workflow de boucle externe qui s’étend sur l’ensemble du cycle DevOps, chaque développeur doit, sur sa propre machine, coder l’application à l’aide de la plateforme et du langage de son choix, puis la tester localement (figure 4-21). Dans tous les cas, les développeurs auront tous un important point en commun, quels que soient le langage, le framework et la plateforme qu’ils auront choisis. Dans ce workflow, vous allez également développer et tester des conteneurs Docker, mais localement.

![Étape 1 : Coder/Exécuter/Déboguer](./media/image18.png)

**Figure 4-21**. Contexte du développement de boucle interne

Le conteneur ou l’instance d’une image Docker contiennent les composants suivants :

- Un choix de système d’exploitation (par exemple, une distribution Linux ou Windows)

- Des fichiers ajoutés par le développeur (par exemple, des binaires d’application)

- Des informations de configuration (par exemple, des paramètres d’environnement et des dépendances)

- Instructions sur les processus que Docker doit exécuter

Vous pouvez configurer le workflow du développement de boucle interne qui utilise Docker comme processus (qui est décrit dans la section suivante). Les premières étapes de configuration de l’environnement ne sont pas incluses, car elles ne doivent être effectuées qu’une seule fois.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Création d’une application dans un conteneur Docker à l’aide de Visual Studio Code et de l’interface CLI Docker

Les applications se composent de vos propres services et de bibliothèques supplémentaires (dépendances).

La figure 4-22 montre les étapes de base que vous devez généralement effectuer lors de la création d’une application Docker, et fournit une description détaillée de chaque étape.

![Vue d’ensemble du workflow : Étape 1 : Coder, Étape 2 : Écrire des fichiers Dockerfile, Étape 3 : Créer des images définies avec des fichiers Dockerfile, Étape 4 : Définir des services avec le fichier docker-compose, Étape 5 : Exécuter des conteneurs ou des applications composées, Étape 6 : Tester les applications, Étape 7 : Pousser (push) pour démarrer la boucle externe (pipelines CI/CD) ou continuer le développement](./media/image19.png)

**Figure 4-22**. Workflow général du cycle de vie des applications Docker conteneurisées dans l’interface CLI Docker

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Étape 1 : Commencer à coder dans Visual Studio Code et créer la première base de référence du service ou de l’application

Le développement des applications se déroule de façon similaire avec ou sans Docker. La différence est que, lors du développement, vous déployez et testez l’application ou les services exécutés dans des conteneurs Docker qui sont situés dans votre environnement local (comme une machine virtuelle Linux ou Windows).

**Configuration de votre environnement local**

Avec les dernières versions de Docker pour Mac et Windows, il n’a jamais été aussi facile de développer des applications Docker, car la configuration est très simple.

> [!TIP]
> Pour obtenir des instructions sur la configuration de Docker sur Windows, accédez à <https://docs.docker.com/docker-for-windows/>.
>
>Pour obtenir des instructions sur la configuration de Docker sur Mac, accédez à <https://docs.docker.com/docker-for-mac/>.

Par ailleurs, vous aurez besoin d’un éditeur de code pour développer votre application tout en utilisant l’interface CLI Docker.

Microsoft propose Visual Studio Code, éditeur de code léger et pris en charge sur Mac, Windows et Linux. Il propose également IntelliSense qui fournit une [prise en charge de nombreux langages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python et la plupart des langages modernes), des fonctionnalités de [débogage](https://code.visualstudio.com/Docs/editor/debugging), l’[intégration à Git](https://code.visualstudio.com/Docs/editor/versioncontrol) et la [prise en charge des extensions](https://code.visualstudio.com/docs/extensions/overview). Cet éditeur est parfait pour les développeurs Mac et Linux. Dans Windows, vous pouvez également utiliser l’intégralité de l’application Visual Studio.

> [!TIP]
> Pour obtenir des instructions concernant l’installation de Visual Studio Code sur Windows, Mac ou Linux, accédez à <https://code.visualstudio.com/docs/setup/setup-overview/>.
>
> Pour obtenir des instructions sur la configuration de Docker sur Mac, accédez à <https://docs.docker.com/docker-for-mac/>.

Vous pouvez utiliser l’interface CLI Docker et écrire votre code à l’aide de n’importe quel éditeur de code. Toutefois, l’utilisation de Visual Studio Code avec l’extension Docker facilite la création des fichiers `Dockerfile` et `docker-compose.yml` dans votre espace de travail. Vous pouvez également exécuter des tâches et des scripts à partir de l’IDE de Visual Studio Code pour exécuter des commandes Docker à l’aide de l’interface CLI Docker ci-dessous.

L’extension Docker pour VS Code fournit les fonctionnalités suivantes :

- La génération automatique des fichiers `Dockerfile` et `docker-compose.yml`

- La mise en surbrillance de la syntaxe et des info-bulles pour les fichiers `docker-compose.yml` et `Dockerfile`

- IntelliSense (saisie semi-automatique) pour les fichiers `Dockerfile` et `docker-compose.yml`

- La vérification ou « linting » (erreurs et avertissements) pour les fichiers `Dockerfile`

- L’intégration de la palette de commandes (F1) pour les commandes Docker les plus courantes

- L’intégration de l’explorateur pour la gestion des images et des conteneurs

- Le déploiement des images de DockerHub et des registres de conteneur Azure sur Azure App Service

Pour installer l’extension Docker, appuyez sur Ctrl + Maj + P, tapez `ext install`, puis exécutez la commande Install Extension pour afficher la liste des extensions Marketplace. Ensuite, tapez **docker** pour filtrer les résultats et sélectionnez l’extension Docker Support, comme illustré dans la figure 4-23.

![Vue de l’extension Docker pour VS Code.](./media/image20.png)

**Figure 4-23**. Installation de l’extension Docker dans Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Étape 2 : Créer un fichier DockerFile associé à une image existante (un simple système d’exploitation ou des environnements de développement comme .NET Core, Node.js et Ruby)

Vous aurez besoin qu’un `DockerFile` soit créé pour chaque image personnalisée et déployé pour chaque conteneur. Si votre application est composée d’un seul service personnalisé, vous n’aurez besoin que d’un seul `DockerFile`. Toutefois, si votre application est composée de plusieurs services (comme dans une architecture de microservices), vous aurez besoin d’un `Dockerfile` par service.

Le `DockerFile` est généralement placé dans le dossier racine de votre application ou de votre service. Il contient les commandes dont a besoin Docker pour savoir comment configurer et exécuter l’application ou le service. Vous pouvez créer votre `DockerFile` et l’ajouter à votre projet en même temps que votre code (node.js, .NET Core, etc.). Si vous ne connaissez pas encore bien l’environnement, lisez l’info-bulle suivante.

> [!TIP]
> L’extension Docker peut vous guider lors de l’utilisation des fichiers `Dockerfile` et `docker-compose.yml` associés à vos conteneurs Docker. Vous finirez probablement par écrire ces types de fichiers sans vous aider de cet outil. Toutefois, l’utilisation de l’extension Docker constitue un bon point de départ qui vous permet d’apprendre plus vite.

Dans la figure 4-24, vous pouvez voir comment le fichier docker-compose est ajouté à l’aide de l’extension Docker pour VS Code.

![Vue de l’extension Docker pour VS Code dans la console.](./media/image24.png)

**Figure 4-24**. Fichiers Docker ajoutés à l’aide de la **commande Add Docker files to Workspace**

Lorsque vous ajoutez un fichier DockerFile, vous devez spécifier quelle image Docker de base vous allez utiliser (par exemple, `FROM mcr.microsoft.com/dotnet/core/aspnet`). En général, vous créez votre image personnalisée sur l’image de base que vous pouvez obtenir dans n’importe quel dépôt officiel du [registre Docker Hub](https://hub.docker.com/) (comme une [image pour .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) ou [pour Node.js](https://hub.docker.com/_/node/)).

***Utiliser une image Docker officielle existante***

L’utilisation du dépôt officiel d’une pile de langages avec numéro de version garantit que les mêmes fonctionnalités de langage seront disponibles sur toutes les machines (y compris celles de développement, de test et de production).

Voici un exemple de fichier DockerFile pour un conteneur .NET Core :

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

Dans ce cas, l’image est basée sur la version 2.2 de l’image Docker ASP.NET Core officielle (multi-architecture pour Linux et Windows), comme dans la ligne `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` (pour plus d’informations à ce sujet, consultez la page [Image Docker ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) et la page [Image Docker .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/)).

Dans le fichier DockerFile, vous pouvez également demander à Docker d’écouter le port TCP que vous utiliserez lors de l’exécution (par exemple, le port 80).

Vous pouvez spécifier des paramètres de configuration supplémentaires dans le fichier Dockerfile, en fonction du langage et du framework que vous utilisez. Par exemple, la ligne `ENTRYPOINT` avec `["dotnet", "MySingleContainerWebApp.dll"]` indique à Docker d’exécuter une application .NET Core. Si vous utilisez le SDK et l’interface CLI .NET Core (`dotnet CLI`) pour créer et exécuter l’application .NET, ce paramètre est différent. L’essentiel à retenir est que la ligne ENTRYPOINT et certains autres paramètres varient selon le langage et la plateforme choisis pour votre application.

> [!TIP]
> Pour plus d’informations sur la création d’images Docker pour les applications .NET Core, accédez à <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.
>
> Pour savoir comment créer vos propres images, accédez à <https://docs.docker.com/engine/tutorials/dockerimages/>.

**Utiliser des dépôts d’images multiarch**

Dans un dépôt, un même nom d’image peut contenir des variantes de plateforme, comme une image Linux et une image Windows. Cette fonctionnalité permet aux fournisseurs comme Microsoft (créateurs d’images de base) de créer un dépôt commun pour plusieurs plateformes (Linux et Windows). Par exemple, le dépôt [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) disponible dans le registre Docker Hub assure la prise en charge de Linux et de Windows Nano Server sous le même nom d’image.

Ainsi, quand vous tirez (pull) une image [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) d’un hôte Windows, la variante Windows est tirée, et quand vous tirez le même nom d’image d’un hôte Linux, la variante Linux est tirée.

***Créer votre image de base à partir de zéro***

Vous pouvez créer votre propre image de base Docker à partir de zéro, comme l’explique [cet article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) tiré du site Docker. Ce scénario n’est probablement pas adapté si vous n’êtes pas encore familiarisé avec Docker. Toutefois, si vous souhaitez définir certains aspects de votre propre image de base, vous pouvez le suivre.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Étape 3 : Créer des images Docker personnalisées et y incorporer le service

Vous devrez créer une image pour chaque service personnalisé qui compose votre application. Si votre application n’est composée que d’un seul service ou d’une seule application web, vous n’aurez besoin que d’une seule image.

> [!NOTE]
> Avec le « workflow de boucle externe DevOps », les images sont créées par un processus de génération automatique dès que vous poussez (push) votre code source vers un dépôt Git (intégration continue). Les images sont donc créées dans cet environnement global à partir de votre code source.
>
> Mais avant de choisir l’option de boucle externe, nous devons vérifier que l’application Docker fonctionne correctement, afin de ne pas pousser (push) vers le système de contrôle de code source (Git, etc.) du code qui ne fonctionne pas correctement.
>
> Par conséquent, chaque développeur doit d’abord effectuer l’intégralité du processus de boucle interne pour effectuer des tests localement et continuer à développer jusqu’à ce qu’il souhaite pousser (push) une fonctionnalité complète ou une modification vers le système de contrôle source.

Pour créer une image dans votre environnement local à l’aide du fichier DockerFile, vous pouvez utiliser la commande docker build, comme illustré dans la figure 4-25 (vous pouvez également exécuter `docker-compose up --build` pour les applications composées de plusieurs conteneurs ou services).

![Sortie de console de la build docker-compose, montrant la progression du téléchargement des images.](./media/image25.png)

**Figure 4-25**. Exécuter docker build

Si vous le souhaitez, au lieu d’exécuter directement `docker build` à partir du dossier du projet, vous pouvez d’abord générer un dossier déployable avec les bibliothèques .NET nécessaires, en exécutant les commandes `dotnet publish` puis `docker build`.

Cet exemple crée une image Docker portant le nom `cesardl/netcore-webapi-microservice-docker:first` (`:first` est une balise, par exemple, une version). Vous pouvez effectuer cette étape pour chaque image personnalisée que vous avez besoin de créer pour l’application Docker à plusieurs conteneurs.

Vous pouvez rechercher les images de votre dépôt local (votre machine de développement) à l’aide de la commande docker images (voir figure 4-26).

![Sortie de console de la commande docker images, montrant les images existantes.](./media/image26.png)

**Figure 4-26**. Affichage des images existantes à l’aide de la commande docker images

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Étape 4 : Définir vos services dans docker-compose.yml lors de la création d’une application Docker composée de plusieurs services

Avec le fichier `docker-compose.yml`, vous pouvez définir un ensemble de services à déployer sous la forme d’une application composée, avec les commandes de déploiement décrites dans la section suivante.

Créez ce fichier dans le dossier de solution racine ou principal, dont le contenu doit être similaire à celui illustré dans ce fichier `docker-compose.yml` :

```yml
version: '3.4'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

Dans ce cas particulier, ce fichier définit deux services : le service web (votre service personnalisé) et le service redis (un service de cache bien connu). Étant donné que chaque service sera déployé comme un conteneur, nous devons utiliser une image Docker concrète pour chacun d’eux. Pour ce service web en particulier, l’image doit :

- Être créée à partir du fichier DockerFile dans le répertoire actif

- Transférer le port 80 exposé du conteneur vers le port 81 de la machine hôte

- Monter le répertoire du projet sur l’ordinateur hôte pour coder dans le conteneur, ce qui vous permet de modifier le code sans avoir à recréer l’image

- Lier le service web au service redis

Le service redis utilise la [dernière image redis publique](https://hub.docker.com/_/redis/) tirée (pull) du registre Docker Hub. [redis](https://redis.io/) est un système de cache bien connu qui est utilisé pour les applications côté serveur.

### <a name="step-5-build-and-run-your-docker-app"></a>Étape 5 : Générer et exécuter votre application Docker

Si votre application ne comprend qu’un seul conteneur, vous pouvez l’exécuter en la déployant sur l’hôte Docker (machine virtuelle ou serveur physique). Toutefois, si votre application est composée de plusieurs services, vous devez également la *composer*. Voyons les différentes options.

***Option A : Exécuter un seul conteneur ou service***

Vous pouvez exécuter l’image Docker à l’aide de la commande docker run, comme illustré ici :

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Pour ce déploiement, nous allons rediriger les requêtes envoyées au port 80 vers le port interne 5000. À présent, l’application écoute le port externe 80 au niveau de l’hôte.

***Option B : Composer et exécuter une application à plusieurs conteneurs***

Dans la plupart des scénarios d’entreprise, une application Docker est composée de plusieurs services. Dans ce cas, vous pouvez exécuter la commande `docker-compose up` (figure 4-27), qui utilise le fichier docker-compose.yml que vous avez peut-être créé précédemment. L’exécution de cette commande déploie une application composée avec tous ses conteneurs.

![Sortie de console de la commande docker-compose up.](./media/image27.png)

**Figure 4-27**. Résultats de l’exécution de la commande docker-compose up

Après avoir exécuté `docker-compose up`, déployez votre application et ses conteneurs sur votre hôte Docker (comme illustré à la figure 4-28) dans la représentation de machine virtuelle.

![Machine virtuelle exécutant des applications à plusieurs conteneurs.](./media/image28.png)

**Figure 4-28**. Machine virtuelle avec des conteneurs Docker déployés

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Étape 6 : Tester l’application Docker (localement, sur votre machine virtuelle CD locale)

Cette étape varie en fonction de ce que fait votre application.

Dans une API web .NET Core de type « Hello World » déployée sous la forme d’un conteneur ou d’un service, vous devez simplement accéder au service en fournissant le port TCP qui est spécifié dans le fichier DockerFile.

Pour accéder à votre service si localhost n’est pas activé, vous pouvez trouver l’adresse IP de l’ordinateur à l’aide de cette commande :

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

Sur l’hôte Docker, ouvrez un navigateur et accédez à ce site. Vous devez y voir votre application ou service s’exécuter, comme illustré à la figure 4-29.

![Vue du navigateur montrant la réponse à localhost/API/values.](./media/image29.png)

**Figure 4-29**. Test de l’application Docker localement avec localhost

Notez que le port 80 est utilisé, mais qu’en interne,elle est redirigée vers le port 5000, car c’est ainsi qu’elle a été déployée avec `docker run`, comme nous l’avons vu précédemment.

Vous pouvez tester cela à l’aide de CURL dans le terminal. Dans une installation Docker sur Windows, l’adresse IP par défaut est 10.0.75.1, comme illustré à la figure 4-30.

![Sortie de console après obtention de http://10.0.75.1/API/values avec CURL](./media/image30.png)

**Figure 4-30**. Test de l’application Docker localement avec CURL

**Débogage d’un conteneur exécuté sur Docker**

Visual Studio Code prend en charge le débogage Docker si vous utilisez Node.js et d’autres plateformes telles que les conteneurs .NET Core.

Vous pouvez également déboguer les conteneurs .NET Core ou .NET Framework dans Docker si vous utilisez Visual Studio pour Windows ou Mac, comme décrit dans la section suivante.

> [!INFORMATION]
>
> Pour plus d’informations sur le débogage des conteneurs Docker Node.js, accédez à <https://blog.docker.com/2016/07/live-debugging-docker/> et <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.

>[!div class="step-by-step"]
>[Précédent](docker-apps-development-environment.md)
>[Suivant](visual-studio-tools-for-docker.md)
