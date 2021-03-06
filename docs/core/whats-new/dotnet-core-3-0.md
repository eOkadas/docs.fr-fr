---
title: Nouveautés de .NET Core 3.0
description: Découvrez les nouvelles fonctionnalités de .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 09/22/2019
ms.openlocfilehash: ddb758b942099657708e79b590c7817c309396d7
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216265"
---
# <a name="whats-new-in-net-core-30"></a>Nouveautés de .NET Core 3.0

Cet article décrit les nouveautés de .NET Core 3,0. Une des principales améliorations est la prise en charge des applications de bureau Windows (Windows uniquement). En utilisant le composant du SDK .NET Core 3.0 Windows Desktop, vous pouvez porter vos applications Windows Forms et Windows Presentation Foundation (WPF). Pour être clair, le composant Windows Desktop est pris en charge et inclus seulement sur Windows. Pour plus d’informations, consultez la section [Bureau Windows](#windows-desktop) plus loin dans cet article.

.NET Core 3.0 prend en charge C# 8.0. Il est fortement recommandé d’utiliser [Visual Studio 2019 16,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), [Visual Studio pour Mac 8,3](/visualstudio/mac/install-preview)ou [Visual Studio code](https://code.visualstudio.com/) avec l'  **C# extension**.

[Téléchargez et commencez à utiliser .net Core 3,0](https://aka.ms/netcore3download) pour le moment sur Windows, MacOS ou Linux.

Pour plus d’informations sur la version, consultez l' [annonce de .net Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).

.NET Core RC1 a été considéré comme une production prête par Microsoft et a été entièrement pris en charge. Si vous utilisez une version préliminaire, vous devez passer à la version RTM pour une prise en charge continue.

## <a name="net-core-sdk-windows-installer"></a>Windows Installer pour le kit SDK .NET Core

Le programme d’installation MSI pour Windows a changé à compter de .NET Core 3.0. Les programmes d’installation du SDK mettent désormais à niveau les versions des plages de fonctionnalités du SDK. Les plages de fonctionnalités sont définies dans les groupes *hundreds* de la section *patch* du numéro de version. Par exemple, **3.0._101_** et **3.0._201_** sont des versions dans deux plages de fonctionnalités différentes, tandis que **3.0._101_** et **3.0._199_** se trouvent dans la même plages de fonctionnalités. En outre, quand le SDK .NET Core **3.0._101_** est installé, le SDK .NET Core **3.0._100_** est supprimé de la machine s’il existe. Quand le SDK .NET Core **3.0._200_** est installé sur la même machine, le SDK .NET Core **3.0._101_** n’est pas supprimé.

Pour plus d’informations sur la gestion des versions, consultez [Vue d’ensemble de la gestion des versions .NET Core](../versions/index.md).

## <a name="c-80"></a>C# 8.0

C#8,0 fait également partie de cette version, qui comprend la fonctionnalité de types de référence Nullable, les flux asynchrones et plus de modèles. Pour plus d’informations sur les fonctionnalités de C# 8.0, consultez [Nouveautés de C# 8.0](../../csharp/whats-new/csharp-8.md).

## <a name="net-standard-21"></a>.NET Standard 2.1

Même si .net Core 3,0 prend en charge **.NET standard 2,1**, `dotnet new classlib` le modèle par défaut génère un projet qui cible toujours **.NET standard 2,0**. Pour cibler **.NET Standard 2.1**, modifiez votre fichier projet et définissez la propriété `TargetFramework` sur `netstandard2.1` :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

Si vous utilisez Visual Studio, vous avez besoin de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), car Visual Studio 2017 ne prend pas en charge **.NET Standard 2.1** ou **.NET Core 3.0**.

## <a name="improved-net-core-version-apis"></a>API de version de .NET Core améliorées

À compter de .NET Core 3.0, les API de version fournies avec .NET Core retournent les informations souhaitées. Par exemple :

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> Modification avec rupture. Il s’agit techniquement d’une modification avec rupture, car le schéma de gestion de version a changé.

## <a name="net-platform-dependent-intrinsics"></a>Intrinsèques dépendant de la plateforme .NET

Des API ont été ajoutées, qui permettent d’accéder à certaines instructions de l’UC orientées performances, comme les ensembles **SIMD** ou les ensembles d’**instructions de manipulation de bits**. Ces instructions peuvent améliorer les performances dans certains scénarios de matière significative, comme le traitement efficace de données en parallèle.

Le cas échéant, les bibliothèques .NET ont commencé à utiliser ces instructions pour améliorer les performances.

Pour plus d’informations, consultez [Intrinsèques dépendant de la plateforme .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).

## <a name="default-executables"></a>Exécutables par défaut

.NET Core génère désormais des [exécutables dépendant du framework](../deploying/index.md#framework-dependent-executables-fde) par défaut. Ce comportement est nouveau pour les applications qui utilisent une version .NET Core installée de façon globale. Auparavant, seuls les [déploiements autonomes](../deploying/index.md#self-contained-deployments-scd) produisaient un exécutable.

Lors de l’étape `dotnet build` ou `dotnet publish`, un exécutable est créé, qui correspond à l’environnement et à la plateforme du Kit de développement que vous utilisez. Vous pouvez obtenir le même résultat avec ces exécutables, comme vous le feriez avec d’autres exécutables natifs comme :

- Vous pouvez double-cliquer sur l’exécutable.
- Vous pouvez lancer l’application directement à partir d’une invite de commandes, par exemple `myapp.exe` sous Windows, et `./myapp` sous Linux et macOS.

## <a name="single-file-executables"></a>Exécutable monofichier

La commande `dotnet publish` prend en charge l’empaquetage de votre application dans un exécutable monofichier spécifique de la plateforme. L’exécutable est auto-extractible et contient toutes les dépendances (y compris natives) nécessaires à l’exécution de votre application. Lors de la première exécution de l’application, celle-ci est extraite d’un répertoire basé sur le nom de l’application et l’identificateur de la build. Le démarrage est plus rapide quand l’application est réexécutée. L’application n’a pas besoin de s’extraire elle-même une deuxième fois, sauf si une nouvelle version a été utilisée.

Pour publier un exécutable monofichier, définissez `PublishSingleFile` dans votre projet ou sur la ligne de commande avec la commande `dotnet publish` :

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

\- ou -

```dotnetcli
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

Pour plus d’informations sur la publication monofichier, consultez le [document conceptuel sur l’outil de regroupement monofichier](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).

## <a name="assembly-linking"></a>Liaison d’assemblys

Le SDK .NET Core 3.0 est fourni avec un outil qui peut réduire la taille des applications en analysant le langage intermédiaire et en supprimant les assemblys inutilisés.

Les applications autonomes incluent tous les éléments nécessaires pour exécuter votre code, sans nécessiter que .NET soit installé sur la machine hôte. Toutefois, il arrive souvent que l’application nécessite seulement un petit sous-ensemble de l’infrastructure pour fonctionner, et que les autres bibliothèques inutilisées puissent être supprimées.

.NET Core inclut désormais un paramètre qui utilisera l’outil [Éditeur de liens de langage intermédiaire](https://github.com/mono/linker) analyser le langage intermédiaire de votre application. Cet outil détecte ce que le code nécessite et supprime les bibliothèques inutilisées. Cet outil peut réduire considérablement la taille de déploiement de certaines applications.

Pour activer cet outil, ajoutez le paramètre `<PublishTrimmed>` dans votre projet et publiez une application autonome :

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

Par exemple, le nouveau modèle de projet de console de base « hello world » inclus, lors de sa publication, atteint la taille d’environ 70 Mo. Avec `<PublishTrimmed>`, sa taille est réduite à environ 30 Mo.

Il est important de prendre en compte le fait que les applications ou infrastructures (dont ASP.NET Core et WPF) qui utilisent la réflexion ou des fonctionnalités dynamiques associées cesseront souvent de fonctionner après cette troncature. Cette rupture se produit car l’éditeur de liens ne connaît pas ce comportement dynamique et ne peut pas déterminer les types de framework nécessaires pour la réflexion. L’outil d’éditeur de liens de langage intermédiaire peut être configuré pour être conscient de ce scénario.

Avant toute chose, veillez à tester votre application après réduction.

Pour plus d’informations sur l’outil d’éditeur de liens de langage intermédiaire, consultez la [documentation](https://aka.ms/dotnet-illink) ou visitez le référentiel [mono/linker]( https://github.com/mono/linker).

## <a name="tiered-compilation"></a>Compilation hiérarchisée

La [compilation hiérarchisée](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) est activée par défaut avec .NET Core 3.0. Cette fonctionnalité permet au runtime d’utiliser de manière plus adaptative le compilateur juste-à-temps (Just-In-Time ou JIT) pour obtenir de meilleures performances.

Le principal avantage de la compilation hiérarchisée est d’autoriser les méthode (re-) JIT avec un niveau de moins bonne qualité mais plus rapide, ou avec un niveau de meilleure qualité mais plus lent. Cela permet d’améliorer les performances d’une application quand elle passe par les différents stades de l’exécution, du démarrage à l’état stable. Ceci contraste avec l’approche de la compilation non hiérarchisée, où chaque méthode est compilée d’une seule manière (la même que le niveau de qualité supérieure), qui privilégie la stabilité de l’état au détriment des performances au démarrage.

Pour activer Quick JIT (code JIT de niveau 0), utilisez ce paramétrage dans votre fichier projet :

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

Pour désactiver complètement la compilation hiérarchisée, utilisez ce paramétrage dans votre fichier projet :

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a>Images ReadyToRun

Vous pouvez améliorer le temps de démarrage de votre application .NET Core en compilant les assemblys de votre application au format ReadyToRun (R2R). R2R est une forme de compilation ahead-of-time (AOT).

Les fichiers binaires R2R améliorent les performances de démarrage en réduisant la quantité de travail que le compilateur juste-à-temps (JIT) doit faire lorsque votre application est chargée. Les fichiers binaires contiennent du code natif similaire à ce que la compilation JIT produirait. Cependant, les fichiers binaires R2R sont plus grands, car ils contiennent à la fois le code du langage intermédiaire (IL), qui est toujours nécessaire pour certains scénarios, et la version native du même code. R2R est disponible seulement quand vous publiez une application autonome qui cible des environnements d’exécution spécifiques (RID), comme Linux x64 ou Windows x64.

Pour compiler votre projet en ReadyToRun, procédez comme suit :

01. Ajoutez le paramètre `<PublishReadyToRun>` à votre projet

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. Publiez une application autonome. Par exemple, cette commande crée une application autonome pour la version 64 bits de Windows :

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained true
    ```

### <a name="cross-platformarchitecture-restrictions"></a>Restrictions d’architecture/de multiplateforme

Le compilateur ReadyToRun ne prend actuellement pas en charge le ciblage croisé. Vous devez compiler sur une cible donnée. Par exemple, si vous souhaitez avoir des images R2R Windows x64, vous devez exécuter la commande de publication sur cet environnement.

Exceptions au ciblage croisé :

- Windows x64 peut être utilisé pour compiler des images Windows ARM32, ARM64 et x86.
- Windows x86 peut être utilisé pour compiler des images Windows ARM32.
- Linux x64 peut être utilisé pour compiler des images Linux ARM32 et ARM64.

## <a name="build-copies-dependencies"></a>Dépendances de copies de build

La commande `dotnet build` copie maintenant les dépendances NuGet pour votre application à partir du cache NuGet vers le dossier de sortie de build. Auparavant, les dépendances étaient copiées uniquement dans le cadre de `dotnet publish`.

Certaines opérations, par exemple la liaison et la publication d’une page de type Razor, nécessiteront toujours une publication.

## <a name="local-tools"></a>Outils locaux

.NET Core 3.0 introduit des outils locaux. Les outils locaux sont similaires aux [outils globaux](../tools/global-tools.md), mais ils sont associés à un emplacement particulier sur le disque. Les outils locaux ne sont pas disponibles globalement et sont distribués en tant que packages NuGet.

> [!WARNING]
> Si vous avez essayé des outils locaux dans .NET Core 3.0 Preview 1, par exemple pour exécuter `dotnet tool restore` ou `dotnet tool install`, supprimez le dossier de cache des outils locaux. Sinon, les outils locaux ne fonctionneront sur aucune nouvelle version. Ce dossier se trouve à ces emplacements :
>
> Sur macOS, Linux : `rm -r $HOME/.dotnet/toolResolverCache`
>
> Sur Windows : `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`

Les outils locaux s’appuient sur un nom de fichier manifeste `dotnet-tools.json` dans votre répertoire actuel. Ce fichier manifeste définit les outils qui doivent être disponibles dans ce dossier et sous-celui-ci. Vous pouvez distribuer le fichier manifeste avec votre code pour que toute personne qui utilise votre code puisse restaurer et utiliser les mêmes outils.

Pour les outils locaux et globaux, une version compatible du runtime est requise. De nombreux outils actuellement sur NuGet.org ciblent le runtime .NET Core 2.1. Pour installer ces outils de façon locale ou globale, vous devez toujours installer le [runtime NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

## <a name="major-version-roll-forward"></a>Restauration par progression d’une version majeure

.NET Core 3.0 introduit une fonctionnalité que vous pouvez choisir d’utiliser et qui permet de restaurer par progression votre application vers la dernière version majeure de .NET Core. En outre, un nouveau paramètre a été ajouté pour contrôler la façon dont la restauration par progression est appliquée à votre application. Ce paramètre peut être configuré des façons suivantes :

- Propriété du fichier projet : `RollForward`
- Propriété du fichier config du runtime : `rollForward`
- Variable d’environnement : `DOTNET_ROLL_FORWARD`
- Argument de ligne de commande : `--roll-forward`

L’une des valeurs suivantes doit être spécifiée. Si le paramètre est omis, **Minor** est la valeur par défaut.

- **LatestPatch**\
Restauration par progression vers la version de correctif la plus élevée. Cette valeur désactive la restauration par progression d’une version mineure.
- **Minor**\
Restauration par progression vers la version mineure supérieure la plus basse, si la version mineure demandée est manquante. Si la version mineure demandée est présente, la stratégie **LatestPatch** est utilisée.
- **Major**\
Restauration par progression vers la version majeure supérieure la plus basse, et la version mineure la plus basse, si la version majeure demandée est manquante. Si la version majeure demandée est présente, la stratégie **Minor** est utilisée.
- **LatestMinor**\
Restauration par progression vers la version mineure la plus élevée, si la version mineure demandée est présente. Conçu pour les scénarios d’hébergement de composant.
- **LatestMajor**\
Restauration par progression vers la version majeure la plus élevée et la version mineure la plus élevée, si la version majeure demandée est présente. Conçu pour les scénarios d’hébergement de composant.
- **Disable**\
Ne pas effectuer de restauration par progression. Lier uniquement à la version spécifiée. Cette stratégie n’est pas recommandée pour une utilisation générale, car elle désactive la possibilité d’effectuer une restauration par progression vers les derniers correctifs. Cette valeur est recommandée uniquement à des fins de test.

Outre le paramètre **Disable**, tous les paramètres utilisent la version de correctif disponible la plus élevée.

## <a name="windows-desktop"></a>Bureau Windows

.NET Core 3.0 prend en charge les applications de bureau Windows utilisant Windows Presentation Foundation (WPF) et Windows Forms. Ces infrastructures prennent également en charge l’utilisation de contrôles modernes et le style Fluent à partir de la bibliothèque XAML de l’interface utilisateur Windows (WinUI) via des [îles XAML](/windows/uwp/xaml-platform/xaml-host-controls).

Le composant Bureau Windows fait partie du SDK .NET Core 3.0 Windows.

Vous pouvez créer une nouvelle application WPF ou Windows Forms à l’aide des commandes `dotnet` suivantes :

```dotnetcli
dotnet new wpf
dotnet new winforms
```

Visual Studio 2019 ajoute des modèles **Nouveau projet** pour Windows Forms et WPF .NET Core 3.0.

Pour plus d’informations sur la façon de porter une application .NET Framework existante, consultez [Porter des projets WPF](../porting/wpf.md) et [Porter des projets Windows Forms](../porting/winforms.md).

## <a name="com-callable-components---windows-desktop"></a>Composants appelables par COM : Windows Desktop

Sur Windows, vous pouvez maintenant créer des composants gérés appelables par COM. Cette fonctionnalité est essentielle pour utiliser .NET Core avec les modèles de compléments COM et également pour assurer la parité avec .NET Framework.

Contrairement à .NET Framework, où *mscoree.dll* était utilisé comme serveur COM, .NET Core ajoute une dll de lanceur natif au répertoire *bin* quand vous générez votre composant COM.

Pour obtenir un exemple montrant comment créer un composant COM et le consommer, consultez la [démonstration COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).

## <a name="msix-deployment---windows-desktop"></a>Déploiement MSIX : Windows Desktop

[MSIX](https://docs.microsoft.com/windows/msix/) est un nouveau format de package d’application Windows. Il peut être utilisé pour déployer des applications de poste de travail .NET Core 3.0 pour Windows 10.

Le [projet de package d’application Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), disponible dans Visual Studio 2019, vous permet de créer des packages MSIX avec des applications .NET Core [autonomes](../deploying/index.md#self-contained-deployments-scd).

Le fichier projet .NET Core doit spécifier les runtimes pris en charge dans la propriété `<RuntimeIdentifiers>` :

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-high-dpi"></a>Haute résolution WinForms

Les applications Windows Forms .NET Core peuvent définir le mode de haute résolution avec <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>. La méthode `SetHighDpiMode` définit le mode de haute résolution correspondant, sauf si le paramètre a été défini par d’autres moyens, comme `App.Manifest` ou P/Invoke avant `Application.Run`.

Les valeurs `highDpiMode` possibles, telles qu’exprimées par l’enum <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType>, sont les suivantes :

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

Pour plus d’informations sur les modes de haute résolution, consultez [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows) (Développement d’applications de bureau haute résolution sur Windows).

## <a name="ranges-and-indices"></a>Plages et index

Le nouveau type <xref:System.Index?displayProperty=nameWithType> peut être utilisé pour l’indexation. Vous pouvez en créer un à partir d’un `int` qui compte à partir du début, ou avec un opérateur (C#) `^` préfixé qui compte à partir de la fin :

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Il existe également le type <xref:System.Range?displayProperty=nameWithType>, composé de deux valeurs `Index`, une pour le début et une pour la fin, et qui peut être écrit avec une expression de plage (C#) `x..y`. Vous pouvez indexer ensuite avec un `Range`, ce qui génère une tranche :

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

Pour plus d’informations, consultez le [tutoriel sur les plages et les index](../../csharp/tutorials/ranges-indexes.md).

## <a name="async-streams"></a>Flux asynchrones

Le type <xref:System.Collections.Generic.IAsyncEnumerable%601> est une nouvelle version asynchrone de <xref:System.Collections.Generic.IEnumerable%601>. Le langage vous permet d’utiliser `await foreach` sur `IAsyncEnumerable<T>` pour consommer ses éléments, et `yield return` sur ceux-ci pour produire des éléments.

L’exemple suivant montre la production et la consommation de flux de données asynchrones. L’instruction `foreach` est asynchrone et utilise elle-même `yield return` afin de produire un flux asynchrone pour les appelants. Ce modèle (qui utilise `yield return`) est le modèle recommandé pour produire des flux de données asynchrones.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

Outre la possibilité d’effectuer une opération `await foreach`, vous pouvez également créer des itérateurs asynchrones, par exemple un itérateur qui retourne un objet `IAsyncEnumerable/IAsyncEnumerator` auquel vous pouvez à la fois appliquer des opérations `await` et `yield`. Pour les objets qui doivent être supprimés, vous pouvez utiliser `IAsyncDisposable`, qui implémentent différents types BCL, notamment `Stream` et `Timer`.

Pour plus d’informations, consultez le [tutoriel sur les flux asynchrones](../../csharp/tutorials/generate-consume-asynchronous-stream.md).

## <a name="ieee-floating-point-improvements"></a>Améliorations apportées à la virgule flottante IEEE

Les API de virgule flottante sont en cours de mise à jour pour devenir conformes à la [révision 754-2008 d’IEEE](https://en.wikipedia.org/wiki/IEEE_754-2008_revision). L’objectif de ces modifications est d’exposer toutes les opérations **obligatoires** et de garantir que leur comportement est conforme à la spécification IEEE. Pour plus d’informations sur les améliorations apportées aux opérations à virgule flottante, consultez le billet de blog [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/).

Les correctifs de l’analyse et de la mise en forme comprennent :

- Analyse et arrondi corrects des entrées, quelle que soit leur longueur.
- Analyse et mise en forme correctes des zéros négatifs.
- Analyse correcte de `Infinity` et `NaN` en effectuant une vérification sans tenir compte de la casse et en autorisant un signe `+` facultatif de début là où c’est applicable.

Les nouvelles API <xref:System.Math?displayProperty=nameWithType> incluent :

- <xref:System.Math.BitIncrement(System.Double)> et <xref:System.Math.BitDecrement(System.Double)>\
Correspond aux opérations IEEE `nextUp` et `nextDown`. Elles retournent le plus petit nombre à virgule flottante dont la valeur est supérieure ou inférieure à l’entrée (respectivement). Par exemple, `Math.BitIncrement(0.0)` retourne `double.Epsilon`.

- <xref:System.Math.MaxMagnitude(System.Double,System.Double)> et <xref:System.Math.MinMagnitude(System.Double,System.Double)>\
Correspond aux opérations IEEE `maxNumMag` et `minNumMag`. Elles retournent la valeur la plus grande ou la plus petite des deux entrées (respectivement). Par exemple, `Math.MaxMagnitude(2.0, -3.0)` retourne `-3.0`.

- <xref:System.Math.ILogB(System.Double)>\
Correspond à l’opération IEEE `logB` qui retourne une valeur intégrale ; elle retourne le logarithme de base 2 intégral du paramètre d’entrée. Cette méthode est identique à `floor(log2(x))`, mais effectuée avec une erreur d’arrondi minimale.

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
Correspond à l’opération IEEE `scaleB` qui prend une valeur intégrale ; elle retourne `x * pow(2, n)`, mais est effectuée avec une erreur d’arrondi minimale.

- <xref:System.Math.Log2(System.Double)>\
Correspond à l’opération IEEE `log2` ; elle retourne le logarithme de base 2. Son erreur d’arrondi est minimale.

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
Correspond à l’opération IEEE `fma` ; elle effectue une multiplication-addition fusionnée. Elle effectue `(x * y) + z` comme une seule opération, avec une erreur d’arrondi minimale. Par exemple, `FusedMultiplyAdd(1e308, 2.0, -1e308)` retourne `1e308`. L’opération régulière `(1e308 * 2.0) - 1e308` retourne `double.PositiveInfinity`.

- <xref:System.Math.CopySign(System.Double,System.Double)>\
Correspond à l’opération IEEE `copySign` ; elle retourne la valeur de `x`, mais avec le signe de `y`.

## <a name="fast-built-in-json-support"></a>Prise en charge JSON intégrée rapide

Les utilisateurs de .NET se sont largement appuyés sur [**Json.NET**](https://www.newtonsoft.com/json) et d’autres bibliothèques JSON populaires, qui restent de bons choix. **Json.NET** utilise des chaînes .NET comme type de données de base, au format UTF-16.

La nouvelle prise en charge JSON intégrée offre des hautes performances et une allocation faible, et elle est basée sur `Span<byte>`. Trois nouveaux types principaux liés à JSON ont été ajoutés à l’espace de noms <xref:System.Text.Json?displayProperty=nameWithType> de .NET Core 3.0. Ces types ne prennent pas *encore* en charge la sérialisation et la désérialisation des objets CLR traditionnels (OCT).

### <a name="utf8jsonreader"></a>Utf8JsonReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> est un lecteur hautes performances et à faible allocation de type forward-only pour le texte JSON codé au format UTF-8 et lu à partir de `ReadOnlySpan<byte>`. `Utf8JsonReader` est un type fondamental de bas niveau, permettant de générer des analyseurs et des désérialiseurs personnalisés. La lecture d’une charge utile JSON à l’aide du nouveau `Utf8JsonReader` est 2 fois plus rapide qu’avec le lecteur proposé par **Json.NET**. Aucune allocation n’a lieu tant que vous n’avez pas besoin d’actualiser des jetons JSON sous forme de chaînes (UTF-16).

Voici un exemple de lecture par le biais du fichier [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) créé par Visual Studio Code :

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a>Utf8JsonWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> fournit un moyen d’écrire du texte JSON encodé en UTF-8 partir de types .NET courants, comme `String`, `Int32`, et `DateTime`, avec des hautes performances, sans mise en cache et vers l’avant uniquement. Comme le lecteur, l’enregistreur (writer) est un type fondamental de bas niveau, permettant de générer des sérialiseurs personnalisés. L’écriture d’une charge utile JSON avec le nouveau `Utf8JsonWriter` est de 30 à 80 % plus rapide qu’avec l’enregistreur (writer) de **Json.NET** et elle n’effectue pas d’allocation.

### <a name="jsondocument"></a>JsonDocument

<xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> est basé sur le `Utf8JsonReader`. Le `JsonDocument` fournit la possibilité d’analyser les données JSON et de générer un modèle DOM (Document Object Model) qui peut être interrogé, et prendre en charge l’accès aléatoire et l’énumération. Les éléments JSON qui composent les données sont accessibles via le type <xref:System.Text.Json.JsonElement> qui est exposé par le `JsonDocument` comme propriété appelée `RootElement`. Le `JsonElement` contient le tableau et les énumérateurs d’objets JSON, ainsi que des API pour convertir le texte JSON en types .NET courants. L’analyse d’une charge utile JSON classique et l’accès à tous ses membres avec le `JsonDocument` est de 2 à 3 fois plus rapide que **Json.NET**, avec peu d’allocations pour les données de dimension raisonnable (c’est-à-dire, < 1 Mo).

Voici un exemple d’utilisation de `JsonDocument` et de `JsonElement`, qui peut être utilisé comme point de départ :

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

Voici un exemple C# 8.0 de lecture par le biais du fichier [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) créé par Visual Studio Code :

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a>JsonSerializer

<xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> s’appuie sur <xref:System.Text.Json.Utf8JsonReader> et <xref:System.Text.Json.Utf8JsonWriter> pour fournir une option de sérialisation rapide à faible consommation de mémoire quand vous utilisez des fragments et des documents JSON.

Voici un exemple de sérialisation d’un objet dans le format JSON :

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

Voici un exemple de désérialisation d’une chaîne JSON en un objet. Vous pouvez utiliser la chaîne JSON produite par l’exemple précédent :

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a>Améliorations de l’interopérabilité

.NET Core 3.0 améliore l’interopérabilité des API natives.

### <a name="type-nativelibrary"></a>Type : NativeLibrary

<xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> fournit une encapsulation pour le chargement d’une bibliothèque native (à l’aide de la même logique de chargement que .NET Core P/Invoke) et la fourniture des fonctions d’assistance pertinentes telles que `getSymbol`. Pour obtenir un exemple de code, consultez la [démonstration DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/DllMapDemo).

### <a name="windows-native-interop"></a>Interopérabilité native Windows

Windows offre une API native riche sous la forme d’API C plates, de COM et de WinRT. Tandis que .NET Core prend en charge **P/Invoke**, .NET Core 3.0 ajoute la possibilité de **cocréer des API COM** et d’**activer des API WinRT**. Pour obtenir un exemple de code, consultez la [démonstration Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).

## <a name="http2-support"></a>Prise en charge de HTTP/2

Le type <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> prend en charge le protocole HTTP/2. Si HTTP/2 est activé, la version du protocole HTTP est négociée par le biais de TLS/ALPN, et HTTP/2 n’est utilisée que si le serveur le choisit.

Le protocole par défaut reste HTTP/1.1, mais HTTP/2 peut être activé de deux manières différentes. Tout d’abord, vous pouvez définir le message de requête HTTP de sorte à utiliser HTTP/2 :

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

Ensuite, vous pouvez modifier <xref:System.Net.Http.HttpClient> pour utiliser HTTP/2 par défaut :

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

Souvent, lorsque vous développez une application, vous souhaiterez utiliser une connexion non chiffrée. Si vous savez que le point de terminaison cible utilisera HTTP/2, vous pouvez activer les connexions non chiffrées pour HTTP/2. Vous pouvez activer cela en définissant la variable d’environnement `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` sur `1` ou en l’activant dans le contexte de l’application :

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 et OpenSSL 1.1.1 sous Linux

.NET Core tire désormais parti de la [prise en charge de TLS 1.3 dans OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), si disponible dans un environnement donné. Avec TLS 1.3 :

- Les délais de connexion sont améliorés grâce à une réduction des allers-retours requis entre le client et le serveur.
- La sécurité est améliorée en raison de la suppression de différents algorithmes de chiffrement obsolètes et non sécurisés.

.NET Core 3.0 utilise **OpenSSL 1.1.1**, **OpenSSL 1.1.0** ou **OpenSSL 1.0.2** sur un système Linux s’ils sont disponibles. Quand **OpenSSL 1.1.1** est disponible, les types <xref:System.Net.Security.SslStream?displayProperty=nameWithType> et <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> utilisent **TLS 1.3** (sous réserve que le client et le serveur prennent en charge **TLS 1.3**).

>[!IMPORTANT]
>Windows et macOS ne prennent pas encore en charge **TLS 1.3**. .NET Core 3.0 prendra en charge **TLS 1.3** sur ces systèmes d’exploitation dès que de la prise en charge sera disponible.

L’exemple C# 8.0 suivant montre comment .NET Core 3.0 sur Ubuntu 18.10 se connecte à <https://www.cloudflare.com> :

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a>Chiffrements

.NET 3.0 prend en charge les chiffrements **AES-GCM** et **AES-CCM**, implémentés avec <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> et <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectivement. Ces algorithmes sont tous deux des [algorithmes AEAD (Authenticated Encryption with Association Data)](https://en.wikipedia.org/wiki/Authenticated_encryption).

Le code suivant montre l’utilisation du chiffrement `AesGcm` pour chiffrer et déchiffrer des données aléatoires.

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a>Importation/exportation d’une clé de chiffrement

.NET Core 3.0 prend en charge l’importation et l’exportation de clés publiques et privées asymétriques aux formats standard. Vous n’avez pas besoin d’utiliser un certificat X.509.

Tous les types de clés, tels que *RSA*, *DSA*, *ECDsa* et *ECDiffieHellman*, prennent en charge les formats suivants :

- **Clé publique**
  - X.509 SubjectPublicKeyInfo

- **Clé privée**
  - PKCS#8 PrivateKeyInfo
  - PKCS#8 EncryptedPrivateKeyInfo

Les clés RSA prennent également en charge :

- **Clé publique**
  - PKCS#1 RSAPublicKey

- **Clé privée**
  - PKCS#1 RSAPrivateKey

Les méthodes d’exportation produisent des données binaires encodées au format DER, tout comme les méthodes d’importation. Si une clé est stockée au format PEM compatible avec le texte, l’appelant devra décoder le contenu au format base64 avant d’appeler une méthode d’importation.

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

Les fichiers **PKCS#8** peuvent être inspectés avec <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType>, tandis que les fichiers **PFX/PKCS#12** peuvent être inspectés avec <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>. Les fichiers **PFX/PKCS#12** peuvent être manipulés avec <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.

## <a name="serialport-for-linux"></a>SerialPort pour Linux

.NET Core 3.0 offre une prise en charge de base de <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> sur Linux.

Auparavant, .NET Core était uniquement pris en charge au moyen de `SerialPort` sur Windows.

Pour plus d’informations sur la prise en charge limitée du port série sur Linux, consultez [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).

## <a name="docker-and-cgroup-memory-limits"></a>Docker et limites de mémoire cgroup

L’exécution de .NET Core 3,0 sur Linux avec l’arrimeur fonctionne mieux avec les limites de mémoire cgroup. L’exécution d’un conteneur Docker avec des limites de mémoire, par exemple avec `docker run -m`, change le comportement de .NET Core.

- Taille de tas par défaut du récupérateur de mémoire (GC) : au maximum 20 Mo ou 75 % de la limite de mémoire sur le conteneur.
- Une taille explicite peut être définie sous forme de nombre absolu ou de pourcentage de la limite cgroup.
- La taille de segment réservée minimale par tas GC est de 16 Mo. Cette taille réduit le nombre de segments de mémoire qui sont créés sur les machines.

## <a name="smaller-garbage-collection-heap-sizes"></a>Tailles de tas de garbage collection plus petites

La taille de tas par défaut du récupérateur de mémoire a été réduite, aboutissant à une diminution de la quantité de mémoire utilisée par .NET Core. Ce changement est plus conforme au budget d’allocation de génération 0 avec les tailles des caches des processeurs modernes.

## <a name="garbage-collection-large-page-support"></a>Prise en charge de grandes pages du garbage collection

Les grandes pages (également appelées HugePages sur Linux) sont une fonctionnalité qui permet au système d’exploitation d’établir des régions de mémoire plus grandes que la taille de page native (souvent 4 Ko) pour améliorer les performances de l’application qui demande ces grandes pages.

Vous pouvez maintenant configurer le récupérateur de mémoire avec la définition **GCLargePages** en tant que fonctionnalité que vous pouvez choisir d’utiliser et qui permet d’allouer de grandes pages sur Windows.

## <a name="gpio-support-for-raspberry-pi"></a>Prise en charge de GPIO pour Raspberry Pi

Deux packages ont été publiés sur NuGet, que vous pouvez utiliser pour la programmation de GPIO :

- [System.Device.Gpio](https://www.nuget.org/packages/System.Device.Gpio)
- [Iot.Device.Bindings](https://www.nuget.org/packages/Iot.Device.Bindings)

Les packages GPIO incluent des API pour les appareils *GPIO*, *SPI*, *I2C* et *PWM*. Le package de liaisons IoT comprend des liaisons d’appareil. Pour plus d’informations, consultez le [dépôt GitHub devices](https://github.com/dotnet/iot/blob/master/src/devices/).

## <a name="arm64-linux-support"></a>Support ARM64 Linux

.NET Core 3.0 prend en charge ARM64 pour Linux. Actuellement, ARM64 est principallement utilisé dans des scénarios IoT. Pour plus d’informations, consultez [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).

Des [images Docker pour .NET Core sur ARM64](https://hub.docker.com/r/microsoft/dotnet/) sont disponibles pour Alpine, Debian et Ubuntu.

> [!NOTE]
> La prise en charge d’**ARM64** sous Windows n’est pas encore disponible.
