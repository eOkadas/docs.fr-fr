---
title: 'Procédure : Créer un assembly à fichier unique .NET Framework'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98f06e62e1070f78faa77ef7d83fd80a62984684
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991250"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="269c6-102">Procédure : Créer un assembly à fichier unique .NET Framework</span><span class="sxs-lookup"><span data-stu-id="269c6-102">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="269c6-103">Un assembly à fichier unique, qui est le type d’assembly le plus simple, contient l’implémentation et les informations de type, ainsi que le [manifeste d’assembly](../../standard/assembly/manifest.md).</span><span class="sxs-lookup"><span data-stu-id="269c6-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="269c6-104">Vous pouvez utiliser des compilateurs de ligne de commande ou Visual Studio pour créer un assembly à fichier unique qui cible le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="269c6-104">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="269c6-105">Par défaut, le compilateur crée un fichier d’assembly avec une extension *. exe* .</span><span class="sxs-lookup"><span data-stu-id="269c6-105">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="269c6-106">Visual Studio pour C# et Visual Basic peut être utilisé uniquement pour créer des assemblys à fichier unique.</span><span class="sxs-lookup"><span data-stu-id="269c6-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="269c6-107">Si vous souhaitez créer des assemblys multifichiers, vous devez utiliser les compilateurs de ligne de commande ou Visual C++.</span><span class="sxs-lookup"><span data-stu-id="269c6-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="269c6-108">Les procédures suivantes montrent comment créer des assemblys à fichier unique à l’aide des compilateurs de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="269c6-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="269c6-109">Créer un assembly avec une extension. exe</span><span class="sxs-lookup"><span data-stu-id="269c6-109">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="269c6-110">À l'invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="269c6-110">At the command prompt, type the following command:</span></span>

<span data-ttu-id="269c6-111">\<*commande_du_compilateur*> \<*nom_du_module*></span><span class="sxs-lookup"><span data-stu-id="269c6-111">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="269c6-112">Dans cette commande, *commande_du_compilateur* est la commande du compilateur pour le langage utilisé dans votre module de code, et *nom_du_module* est le nom du module de code à compiler dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="269c6-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="269c6-113">L’exemple suivant crée un assembly nommé *myCode. exe* à partir d’un `myCode`module de code appelé.</span><span class="sxs-lookup"><span data-stu-id="269c6-113">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="269c6-114">Créer un assembly avec une extension. exe et spécifier le nom du fichier de sortie</span><span class="sxs-lookup"><span data-stu-id="269c6-114">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="269c6-115">À l'invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="269c6-115">At the command prompt, type the following command:</span></span>

<span data-ttu-id="269c6-116">\<*commande_du_compilateur*>  **/out:** \<*nom_du_fichier*> \<*nom_du_module*></span><span class="sxs-lookup"><span data-stu-id="269c6-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="269c6-117">Dans cette commande, *commande_du_compilateur* est la commande du compilateur pour le langage utilisé dans votre module de code, *nom_du_fichier* est le nom du fichier de sortie, et *nom_du_module* est le nom du module de code à compiler dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="269c6-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="269c6-118">L’exemple suivant crée un assembly nommé *myAssembly. exe* à partir d’un `myCode`module de code appelé.</span><span class="sxs-lookup"><span data-stu-id="269c6-118">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="269c6-119">Créer des assemblys de bibliothèque</span><span class="sxs-lookup"><span data-stu-id="269c6-119">Create library assemblies</span></span>
 <span data-ttu-id="269c6-120">Un assembly de bibliothèque est similaire à une bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="269c6-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="269c6-121">Il contient des types qui seront référencés par d’autres assemblys, mais n’a aucun point d’entrée pour commencer l’exécution.</span><span class="sxs-lookup"><span data-stu-id="269c6-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="269c6-122">Pour créer un assembly de bibliothèque, à l’invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="269c6-122">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="269c6-123">\<*commande_du_compilateur*>  **-t:library** \<*nom_du_module*></span><span class="sxs-lookup"><span data-stu-id="269c6-123">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="269c6-124">Dans cette commande, *commande_du_compilateur* est la commande du compilateur pour le langage utilisé dans votre module de code, et *nom_du_module* est le nom du module de code à compiler dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="269c6-124">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="269c6-125">Vous pouvez également utiliser d’autres options du compilateur, telles que l’option **-out:** .</span><span class="sxs-lookup"><span data-stu-id="269c6-125">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="269c6-126">L’exemple suivant crée un assembly de bibliothèque nommé *myCodeAssembly. dll* à partir d' `myCode`un module de code appelé.</span><span class="sxs-lookup"><span data-stu-id="269c6-126">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="269c6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="269c6-127">See also</span></span>

- [<span data-ttu-id="269c6-128">Créer des assemblys</span><span class="sxs-lookup"><span data-stu-id="269c6-128">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="269c6-129">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="269c6-129">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="269c6-130">Guide pratique pour Créer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="269c6-130">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="269c6-131">Programmer avec des assemblys</span><span class="sxs-lookup"><span data-stu-id="269c6-131">Program with assemblies</span></span>](../../standard/assembly/program.md)