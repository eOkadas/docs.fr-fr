---
title: Journalisation avec la pile élastique
description: Journalisation à l’aide de la pile élastique, Logstash et Kibana
ms.date: 09/23/2019
ms.openlocfilehash: b3fd3ea30f46914e6513be79f7d949499142b381
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182831"
---
# <a name="logging-with-elastic-stack"></a><span data-ttu-id="6c21c-103">Journalisation avec la pile élastique</span><span class="sxs-lookup"><span data-stu-id="6c21c-103">Logging with Elastic Stack</span></span> 

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6c21c-104">Il existe de nombreux outils de journalisation centralisés et leur coût est inférieur à celui des outils open source gratuits, à des options plus coûteuses.</span><span class="sxs-lookup"><span data-stu-id="6c21c-104">There are many good centralized logging tools and they vary in cost from being free, open-source tools, to more expensive options.</span></span> <span data-ttu-id="6c21c-105">Dans de nombreux cas, les outils gratuits sont aussi bons ou mieux que les offres payantes.</span><span class="sxs-lookup"><span data-stu-id="6c21c-105">In many cases, the free tools are as good as or better than the paid offerings.</span></span> <span data-ttu-id="6c21c-106">L’un de ces outils est une combinaison de trois composants Open Source : Recherche élastique, Logstash et Kibana.</span><span class="sxs-lookup"><span data-stu-id="6c21c-106">One such tool is a combination of three open-source components: Elastic search, Logstash, and Kibana.</span></span> <span data-ttu-id="6c21c-107">Ces outils sont appelés pile élastique ou pile ELK.</span><span class="sxs-lookup"><span data-stu-id="6c21c-107">Collectively these tools are known as the Elastic Stack or ELK stack.</span></span>

## <a name="what-are-the-advantages-of-elastic-stack"></a><span data-ttu-id="6c21c-108">Quels sont les avantages de la pile élastique ?</span><span class="sxs-lookup"><span data-stu-id="6c21c-108">What are the advantages of Elastic Stack?</span></span>

<span data-ttu-id="6c21c-109">La pile élastique fournit une journalisation centralisée dans une solution cloud conviviale et évolutive.</span><span class="sxs-lookup"><span data-stu-id="6c21c-109">Elastic Stack provides centralized logging in a low-cost, scalable, cloud-friendly manner.</span></span> <span data-ttu-id="6c21c-110">Son interface utilisateur simplifie l’analyse des données, ce qui vous permet de consacrer du temps à la collecte d’informations à partir de vos données au lieu de combattre une interface plus sourde.</span><span class="sxs-lookup"><span data-stu-id="6c21c-110">Its user interface streamlines data analysis so you can spend your time gleaning insights from your data instead of fighting with a clunky interface.</span></span> <span data-ttu-id="6c21c-111">Il prend en charge un large éventail d’entrées, de sorte que votre application distribuée s’étend sur de plus en plus de types de services différents, vous pouvez vous attendre à pouvoir continuer à alimenter le journal et les données de métriques dans le système.</span><span class="sxs-lookup"><span data-stu-id="6c21c-111">It supports a wide variety of inputs so as your distributed application spans more and different kinds of services, you can expect to continue to be able to feed log and metric data into the system.</span></span> <span data-ttu-id="6c21c-112">La pile élastique prend également en charge les recherches rapides, même dans les jeux de données volumineux, ce qui permet aux applications de grande taille de consigner des données détaillées tout en étant en mesure de les visualiser de manière performante.</span><span class="sxs-lookup"><span data-stu-id="6c21c-112">The Elastic Stack also supports fast searches even across large data sets, making it possible to for even large applications to log detailed data and still be able to have visibility into it in a performant fashion.</span></span>

## <a name="logstash"></a><span data-ttu-id="6c21c-113">Logstash</span><span class="sxs-lookup"><span data-stu-id="6c21c-113">Logstash</span></span>

<span data-ttu-id="6c21c-114">Le premier composant est [Logstash](https://www.elastic.co/products/logstash).</span><span class="sxs-lookup"><span data-stu-id="6c21c-114">The first component is [Logstash](https://www.elastic.co/products/logstash).</span></span> <span data-ttu-id="6c21c-115">Cet outil est utilisé pour collecter des informations de journalisation à partir d’une grande variété de sources différentes.</span><span class="sxs-lookup"><span data-stu-id="6c21c-115">This tool is used to gather log information from a large variety of different sources.</span></span> <span data-ttu-id="6c21c-116">Par exemple, Logstash peut lire les journaux à partir du disque et recevoir également des messages des bibliothèques de journalisation telles que [Serilog](https://serilog.net/).</span><span class="sxs-lookup"><span data-stu-id="6c21c-116">For instance, Logstash can read logs from disk and also receive messages from logging libraries like [Serilog](https://serilog.net/).</span></span> <span data-ttu-id="6c21c-117">Logstash peut effectuer un filtrage et une expansion de base sur les journaux au fur et à mesure de leur arrivée.</span><span class="sxs-lookup"><span data-stu-id="6c21c-117">Logstash can do some basic filtering and expansion on the logs as they arrive.</span></span> <span data-ttu-id="6c21c-118">Par exemple, si vos journaux contiennent des adresses IP, Logstash peut être configuré pour effectuer une recherche géographique et obtenir un pays ou même une ville d’origine pour ce message.</span><span class="sxs-lookup"><span data-stu-id="6c21c-118">For instance, if your logs contain IP addresses then Logstash may be configured to do a geographical lookup and obtain a country or even city of origin for that message.</span></span> 

<span data-ttu-id="6c21c-119">Serilog est une bibliothèque de journalisation pour les langages .NET, qui permet la journalisation paramétrée.</span><span class="sxs-lookup"><span data-stu-id="6c21c-119">Serilog is a logging library for .NET languages, which allows for parameterized logging.</span></span> <span data-ttu-id="6c21c-120">Au lieu de générer un message de journalisation qui incorpore des champs, les paramètres sont conservés séparément.</span><span class="sxs-lookup"><span data-stu-id="6c21c-120">Instead of generating a textual log message that embeds fields, parameters are kept separate.</span></span> <span data-ttu-id="6c21c-121">Cela permet un filtrage et une recherche plus intelligents.</span><span class="sxs-lookup"><span data-stu-id="6c21c-121">This allows for more intelligent filtering and searching.</span></span> <span data-ttu-id="6c21c-122">Un exemple de configuration Serilog pour l’écriture dans Logstash apparaît dans la figure 7-2.</span><span class="sxs-lookup"><span data-stu-id="6c21c-122">A sample Serilog configuration for writing to Logstash appears in Figure 7-2.</span></span>

```csharp
var log = new LoggerConfiguration()   
         .WriteTo.Http("http://localhost:8080")
         .CreateLogger();
```

<span data-ttu-id="6c21c-123">**Figure 7-2** Configuration de Serilog pour écrire des informations de journal directement dans logstash sur HTTP</span><span class="sxs-lookup"><span data-stu-id="6c21c-123">**Figure 7-2** Serilog config for writing log information directly to logstash over HTTP</span></span>

<span data-ttu-id="6c21c-124">Logstash utilise une configuration telle que celle illustrée dans la figure 7-3.</span><span class="sxs-lookup"><span data-stu-id="6c21c-124">Logstash would use a configuration like the one shown in Figure 7-3.</span></span> 

```
input {
    http {
        #default host 0.0.0.0:8080
        codec => json
    }
}

output {
    elasticsearch {
        hosts => "elasticsearch:9200"
        index=>"sales-%{+xxxx.ww}"
    }
}
```

<span data-ttu-id="6c21c-125">**Figure 7-3** : configuration Logstash pour la consommation des journaux à partir de Serilog</span><span class="sxs-lookup"><span data-stu-id="6c21c-125">**Figure 7-3** - A Logstash configuration for consuming logs from Serilog</span></span>

<span data-ttu-id="6c21c-126">Dans les scénarios où une manipulation de journal étendue n’est pas nécessaire, il existe une alternative à Logstash appelée [temps](https://www.elastic.co/products/beats).</span><span class="sxs-lookup"><span data-stu-id="6c21c-126">For scenarios where extensive log manipulation isn't needed there's an alternative to Logstash known as [Beats](https://www.elastic.co/products/beats).</span></span> <span data-ttu-id="6c21c-127">Le temps est une famille d’outils qui peuvent recueillir un large éventail de données à partir des journaux vers les données réseau et les informations de temps d’activité.</span><span class="sxs-lookup"><span data-stu-id="6c21c-127">Beats is a family of tools that can gather a wide variety of data from logs to network data and uptime information.</span></span> <span data-ttu-id="6c21c-128">De nombreuses applications utilisent à la fois les Logstash et les temps.</span><span class="sxs-lookup"><span data-stu-id="6c21c-128">Many applications will use both Logstash and Beats.</span></span>

<span data-ttu-id="6c21c-129">Une fois les journaux collectés par Logstash, il faut les placer.</span><span class="sxs-lookup"><span data-stu-id="6c21c-129">Once the logs have been gathered by Logstash, it needs somewhere to put them.</span></span> <span data-ttu-id="6c21c-130">Bien que Logstash prenne en charge de nombreuses sorties différentes, l’une des plus intéressantes est la recherche élastique.</span><span class="sxs-lookup"><span data-stu-id="6c21c-130">While Logstash supports many different outputs, one of the more exciting ones is Elastic search.</span></span>

## <a name="elastic-search"></a><span data-ttu-id="6c21c-131">Recherche élastique</span><span class="sxs-lookup"><span data-stu-id="6c21c-131">Elastic search</span></span>

<span data-ttu-id="6c21c-132">La recherche élastique est un moteur de recherche puissant qui peut indexer les journaux à mesure qu’ils arrivent.</span><span class="sxs-lookup"><span data-stu-id="6c21c-132">Elastic search is a powerful search engine that can index logs as they arrive.</span></span> <span data-ttu-id="6c21c-133">Elle accélère l’exécution des requêtes sur les journaux.</span><span class="sxs-lookup"><span data-stu-id="6c21c-133">It makes running queries against the logs quick.</span></span> <span data-ttu-id="6c21c-134">La recherche élastique peut gérer de grandes quantités de journaux et, dans des cas extrêmes, peut être montée en charge sur plusieurs nœuds.</span><span class="sxs-lookup"><span data-stu-id="6c21c-134">Elastic search can handle huge quantities of logs and, in extreme cases, can be scaled out across many nodes.</span></span> 

<span data-ttu-id="6c21c-135">Les messages de journal qui ont été conçus pour contenir des paramètres ou dont les paramètres ont été fractionnés à l’aide du traitement Logstash peuvent être interrogés directement, car Elasticsearch conserve ces informations.</span><span class="sxs-lookup"><span data-stu-id="6c21c-135">Log messages that have been crafted to contain parameters or that have had parameters split from them through Logstash processing, can be queried directly as Elasticsearch preserves this information.</span></span>

<span data-ttu-id="6c21c-136">Une requête qui recherche les 10 premières pages visitées par `jill@example.com`, apparaît dans la figure 7-4.</span><span class="sxs-lookup"><span data-stu-id="6c21c-136">A query that searches for the top 10 pages visited by `jill@example.com`, appears in Figure 7-4.</span></span>

```
"query": {
    "match": {
      "user": "jill@example.com"
    }
  },
  "aggregations": {
    "top_10_pages": {
      "terms": {
        "field": "page",
        "size": 10
      }
    }
  }
```

<span data-ttu-id="6c21c-137">**Figure 7-4** : requête Elasticsearch pour rechercher les 10 premières pages visitées par un utilisateur</span><span class="sxs-lookup"><span data-stu-id="6c21c-137">**Figure 7-4** - An Elasticsearch query for finding top 10 pages visited by a user</span></span>

## <a name="visualizing-information-with-kibana-web-dashboards"></a><span data-ttu-id="6c21c-138">Visualisation des informations avec les tableaux de bord Web Kibana</span><span class="sxs-lookup"><span data-stu-id="6c21c-138">Visualizing information with Kibana web dashboards</span></span>

<span data-ttu-id="6c21c-139">Le composant final de la pile est Kibana.</span><span class="sxs-lookup"><span data-stu-id="6c21c-139">The final component of the stack is Kibana.</span></span> <span data-ttu-id="6c21c-140">Cet outil est utilisé pour fournir des visualisations interactives dans un tableau de bord Web.</span><span class="sxs-lookup"><span data-stu-id="6c21c-140">This tool is used to provide interactive visualizations in a web dashboard.</span></span> <span data-ttu-id="6c21c-141">Les tableaux de bord peuvent être créés même par des utilisateurs non techniques.</span><span class="sxs-lookup"><span data-stu-id="6c21c-141">Dashboards may be crafted even by users who are non-technical.</span></span> <span data-ttu-id="6c21c-142">La plupart des données qui résident dans l’index Elasticsearch peuvent être incluses dans les tableaux de bord Kibana.</span><span class="sxs-lookup"><span data-stu-id="6c21c-142">Most data that is resident in the Elasticsearch index, can be included in the Kibana dashboards.</span></span> <span data-ttu-id="6c21c-143">Les utilisateurs individuels peuvent avoir différents tableaux de bord, et Kibana permet cette personnalisation en autorisant des tableaux de bord spécifiques à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6c21c-143">Individual users may have different dashboard desires and Kibana enables this customization through allowing user-specific dashboards.</span></span> 

## <a name="installing-elastic-stack-on-azure"></a><span data-ttu-id="6c21c-144">Installation de la pile élastique sur Azure</span><span class="sxs-lookup"><span data-stu-id="6c21c-144">Installing Elastic Stack on Azure</span></span>

<span data-ttu-id="6c21c-145">La pile élastique peut être installée sur Azure de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="6c21c-145">The Elastic stack can be installed on Azure in a number of ways.</span></span> <span data-ttu-id="6c21c-146">Comme toujours, il est possible d' [approvisionner des machines virtuelles et d’y installer directement la pile élastique](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span><span class="sxs-lookup"><span data-stu-id="6c21c-146">As always, it's possible to [provision virtual machines and install Elastic Stack on them directly](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch).</span></span> <span data-ttu-id="6c21c-147">Cette option est recommandée par certains utilisateurs expérimentés, car elle offre le degré de personnalisation le plus élevé.</span><span class="sxs-lookup"><span data-stu-id="6c21c-147">This option is preferred by some experienced users as it offers the highest degree of customizability.</span></span> <span data-ttu-id="6c21c-148">Le déploiement sur infrastructure as a service introduit une surcharge de gestion importante qui oblige les personnes qui utilisent ce chemin d’accès à prendre possession de toutes les tâches associées à infrastructure as a service telles que la sécurisation des ordinateurs et la mise à jour des correctifs.</span><span class="sxs-lookup"><span data-stu-id="6c21c-148">Deploying on infrastructure as a service introduces significant management overhead forcing those who take that path to take ownership of all the tasks associated with infrastructure as a service such as securing the machines and keeping up-to-date with patches.</span></span> 

<span data-ttu-id="6c21c-149">Une option avec moins de surcharge consiste à utiliser l’un des nombreux conteneurs d’ancrage sur lesquels la pile élastique a déjà été configurée.</span><span class="sxs-lookup"><span data-stu-id="6c21c-149">An option with less overhead is to make use of one of the many Docker containers on which the Elastic Stack has already been configured.</span></span> <span data-ttu-id="6c21c-150">Ces conteneurs peuvent être déposés dans un cluster Kubernetes existant et exécutés avec le code d’application.</span><span class="sxs-lookup"><span data-stu-id="6c21c-150">These containers can be dropped into an existing Kubernetes cluster and run alongside application code.</span></span> <span data-ttu-id="6c21c-151">Le conteneur [sebp/Elk](https://elk-docker.readthedocs.io/) est un conteneur de pile élastique bien documenté et testé.</span><span class="sxs-lookup"><span data-stu-id="6c21c-151">The [sebp/elk](https://elk-docker.readthedocs.io/) container is a well-documented and tested Elastic Stack container.</span></span>

<span data-ttu-id="6c21c-152">Une autre option est une [offre de kit en tant que service récemment annoncée](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span><span class="sxs-lookup"><span data-stu-id="6c21c-152">Another option is a [recently announced ELK-as-a-service offering](https://devops.com/logz-io-unveils-azure-open-source-elk-monitoring-solution/).</span></span>

## <a name="references"></a><span data-ttu-id="6c21c-153">Références</span><span class="sxs-lookup"><span data-stu-id="6c21c-153">References</span></span>

- [<span data-ttu-id="6c21c-154">Installer la pile élastique sur Azure</span><span class="sxs-lookup"><span data-stu-id="6c21c-154">Install Elastic Stack on Azure</span></span>](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-elasticsearch)

>[!div class="step-by-step"]
><span data-ttu-id="6c21c-155">[Précédent](observability-patterns.md)
>[Suivant](monitoring-azure-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="6c21c-155">[Previous](observability-patterns.md)
[Next](monitoring-azure-kubernetes.md)</span></span>