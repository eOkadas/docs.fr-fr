---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181796"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Commutateur de compatibilité Switch. System. Windows. Forms. DoNotLoadLatestRichEditControl non pris en charge

Le `Switch.System.Windows.Forms.UseLegacyImages` commutateur de compatibilité, qui a été introduit dans .NET Framework 4.7.1, n’est pas pris en charge dans Windows Forms sur .net Core 3,0.

#### <a name="change-description"></a>Modifier la description

Dans le .NET Framework 4.6.2 et les versions antérieures, <xref:System.Windows.Forms.RichTextBox> le contrôle instancierait le contrôle Win32 RichEdit v 3.0 et, pour les applications qui ciblent .NET Framework <xref:System.Windows.Forms.RichTextBox> 4.7.1, le contrôle instancierait RichEdit v 4.1 (dans  *que dans msftedit. dll*). Le `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` commutateur de compatibilité a été introduit pour permettre aux applications qui ciblent .NET Framework 4.7.1 et versions ultérieures de refuser le nouveau contrôle RichEdit v 4.1 et d’utiliser à la place l’ancien contrôle RichEdit v3.

Dans .net Core, le `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` commutateur n’est pas pris en charge. Seules les <xref:System.Windows.Forms.RichTextBox> nouvelles versions du contrôle sont prises en charge.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 9

#### <a name="recommended-action"></a>Action recommandée

Supprimez le commutateur. Le commutateur n’est pas pris en charge et aucune autre fonctionnalité n’est disponible.

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
