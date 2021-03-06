---
title: Prise en main F# avec les outils en ligne de commande
description: Apprenez à créer une solution à plusieurs projets simple sur F# à l’aide de l’CLI .net Core sur n’importe quel système d’exploitation (Windows, MacOS ou Linux).
ms.date: 03/26/2018
ms.openlocfilehash: f9177e653273e5a2191407c4fb22343ded11fece
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117920"
---
# <a name="get-started-with-f-with-the-net-core-cli"></a>Prise en main F# de avec le CLI .net Core

Cet article explique comment vous pouvez commencer avec F# sur n’importe quel système d’exploitation (Windows, MacOS ou Linux) avec le CLI .net core. Il passe par la création d’une solution à projets multiples avec une bibliothèque de classes appelée par une application console.

## <a name="prerequisites"></a>Prérequis

Pour commencer, vous devez installer la dernière [Kit SDK .net Core](https://dotnet.microsoft.com/download).

Cet article suppose que vous savez comment utiliser une ligne de commande et que vous avez un éditeur de texte préféré. Si vous ne l’utilisez pas déjà, [Visual Studio code](get-started-vscode.md) est une option intéressante en tant qu’éditeur F#de texte pour.

## <a name="build-a-simple-multi-project-solution"></a>Créer une solution à plusieurs projets simple

Ouvrez une invite de commandes/terminal et utilisez la commande [dotnet New](../../core/tools/dotnet-new.md) pour créer un nouveau fichier `FSNetCore`solution appelé :

```dotnetcli
dotnet new sln -o FSNetCore
```

La structure de répertoire suivante est générée après l’exécution de la commande précédente :

```console
FSNetCore
    ├── FSNetCore.sln
```

### <a name="write-a-class-library"></a>Écrire une bibliothèque de classes

Remplacez les répertoires par *FSNetCore*.

Utilisez la `dotnet new` commande, créez un projet de bibliothèque de classes dans le dossier **src** nommé Library.

```dotnetcli
dotnet new classlib -lang F# -o src/Library
```

La structure de répertoire suivante est générée après l’exécution de la commande précédente :

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Remplacez le contenu de `Library.fs` par le code suivant :

```fsharp
module Library

open Newtonsoft.Json

let getJsonNetJson value =
    sprintf "I used to be %s but now I'm %s thanks to JSON.NET!" value (JsonConvert.SerializeObject(value))
```

Ajoutez le package NuGet Newtonsoft. JSON au projet de bibliothèque.

```dotnetcli
dotnet add src/Library/Library.fsproj package Newtonsoft.Json
```

Ajoutez le `Library` projet à la `FSNetCore` solution à l’aide de la commande [dotnet sln Add](../../core/tools/dotnet-sln.md) :

```dotnetcli
dotnet sln add src/Library/Library.fsproj
```

Exécutez `dotnet build` pour générer le projet. Les dépendances non résolues seront restaurées lors de la génération.

### <a name="write-a-console-application-that-consumes-the-class-library"></a>Écrire une application console qui utilise la bibliothèque de classes

Utilisez la `dotnet new` commande, créez une application console dans le dossier **src** nommé App.

```dotnetcli
dotnet new console -lang F# -o src/App
```

La structure de répertoire suivante est générée après l’exécution de la commande précédente :

```console
└── FSNetCore
    ├── FSNetCore.sln
    └── src
        ├── App
        │   ├── App.fsproj
        │   ├── Program.fs
        └── Library
            ├── Library.fs
            └── Library.fsproj
```

Remplacez le contenu du fichier `Program.fs` avec le code suivant :

```fsharp
open System
open Library

[<EntryPoint>]
let main argv =
    printfn "Nice command-line arguments! Here's what JSON.NET has to say about them:"

    argv
    |> Array.map getJsonNetJson
    |> Array.iter (printfn "%s")

    0 // return an integer exit code
```

Ajoutez une référence au `Library` projet à l’aide de [dotnet ajouter une référence](../../core/tools/dotnet-add-reference.md).

```dotnetcli
dotnet add src/App/App.fsproj reference src/Library/Library.fsproj
```

Ajoutez le `App` projet à la `FSNetCore` solution à l' `dotnet sln add` aide de la commande :

```dotnetcli
dotnet sln add src/App/App.fsproj
```

Restaurez les dépendances `dotnet restore` NuGet et `dotnet build` exécutez pour générer le projet.

Accédez au projet de `src/App` console, puis exécutez le projet en `Hello World` passant comme arguments :

```console
cd src/App
dotnet run Hello World
```

Les résultats suivants doivent s’afficher:

```console
Nice command-line arguments! Here's what JSON.NET has to say about them:

I used to be Hello but now I'm ""Hello"" thanks to JSON.NET!
I used to be World but now I'm ""World"" thanks to JSON.NET!
```

## <a name="next-steps"></a>Étapes suivantes

Consultez ensuite la [visite guidée de F# ](../tour.md) pour en savoir plus sur les F# différentes fonctionnalités.
