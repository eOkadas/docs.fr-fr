---
title: E/S sur fichier asynchrones
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET Framework], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b045ad7e9a808b3e2b8d89750001ec9c4a33c005
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170748"
---
# <a name="asynchronous-file-io"></a>E/S sur fichier asynchrones

Les opérations asynchrones vous permettent d'exécuter des opérations d'E/S consommant beaucoup de ressources sans bloquer le thread principal. Cette considération de performance est particulièrement importante dans une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ou une application de bureau où une longue opération de flux peut bloquer le thread d'interface utilisateur et faire que l'application s'affiche comme si elle ne fonctionnait pas.

Depuis .NET Framework 4.5, les types d’E/S incluent des méthodes asynchrones pour simplifier les opérations asynchrones. Une méthode asynchrone contient `Async` dans son nom, comme <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, et <xref:System.IO.TextReader.ReadToEndAsync%2A>. Ces méthodes asynchrones sont implémentées sur les classes de flux, telles que <xref:System.IO.Stream>, <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, et les classes qui sont utilisées pour lire ou écrire dans des flux, comme <xref:System.IO.TextReader> et l' <xref:System.IO.TextWriter>.

Dans .NET Framework 4 et les versions antérieures, on doit utiliser des méthodes telles que <xref:System.IO.Stream.BeginRead%2A> et <xref:System.IO.Stream.EndRead%2A> pour implémenter les opérations d'E/S asynchrones. Ces méthodes sont toujours disponibles dans .NET Framework 4.5 pour prendre en charge le code hérité. Toutefois, les méthodes asynchrones vous aident à implémenter les opérations d’E/S asynchrones plus facilement.

C# et Visual Basic ont chacun deux mots clés pour la programmation asynchrone :

- `Async` (Visual Basic) ou `async` modificateur (C#), qui est utilisé pour marquer une méthode contenant une opération asynchrone.

- `Await` (Visual Basic) ou `await` opérateur (C#), qui est appliqué au résultat d'une méthode asynchrone.

Pour implémenter des opérations d'E/S asynchrones, utilisez ces mots clés conjointement aux méthodes async, comme indiqué dans les exemples suivants. Pour plus d'informations, consultez [Programmation asynchrone avec async et await (C#)](../../csharp/programming-guide/concepts/async/index.md) et [Programmation asynchrone avec Async et Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).

L'exemple suivant montre comment utiliser deux objets <xref:System.IO.FileStream> pour copier des fichiers de façon asynchrone d'un répertoire à un autre. Notez que le gestionnaire d'événements <xref:System.Web.UI.WebControls.Button.Click> pour le contrôle <xref:System.Windows.Controls.Button> est marqué avec le modificateur `async` car il appelle une méthode asynchrone.

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

L'exemple suivant est semblable au précédent, mais utilise des objets <xref:System.IO.StreamReader> et <xref:System.IO.StreamWriter> pour lire et écrire le contenu d'un fichier texte de façon asynchrone.

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

L'exemple suivant montre le fichier code-behind et le fichier XAML utilisés pour ouvrir un fichier comme <xref:System.IO.Stream> dans une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] , et lire son contenu en utilisant une instance de la classe <xref:System.IO.StreamReader> . Il utilise des méthodes asynchrones pour ouvrir le fichier en tant que flux et lire son contenu.

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IO.Stream>
- [Fichier et flux de données E/S](index.md)
- [Programmation asynchrone avec async et await (C#)](../../csharp/programming-guide/concepts/async/index.md)
- [Programmation asynchrone avec Async et Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
