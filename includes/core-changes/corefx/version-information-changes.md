---
ms.openlocfilehash: 2a751acc129ebd1c917b87f8083ffef72c7d8c17
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216370"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>API qui signalent la version du produit et non de la version du fichier

La plupart des API qui retournent des versions dans .NET Core retournaient désormais la version du produit plutôt que la version du fichier.

#### <a name="change-description"></a>Modifier la description

Dans .net Core 2,2 et versions antérieures, les méthodes telles <xref:System.Environment.Version?displayProperty=nameWithType>que <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, et la boîte de dialogue des propriétés de fichier pour les assemblys .net Core reflètent la version de fichier. À compter de .NET Core 3,0, ils reflètent la version du produit.

La figure suivante illustre la différence dans les informations de version de l’assembly *System. Runtime. dll* pour .net Core 2,2 (à gauche) et .net Core 3,0 (à droite), tel qu’affiché dans la boîte de dialogue des propriétés du fichier de l' **Explorateur Windows** .

![Différence dans les informations sur la version du produit](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Aucun. Cette modification doit rendre la détection de version intuitive plutôt que abstruse.

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>API affectées

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
