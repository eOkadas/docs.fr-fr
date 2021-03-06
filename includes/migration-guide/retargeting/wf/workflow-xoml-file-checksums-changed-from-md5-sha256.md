---
ms.openlocfilehash: 19e0524f4d40517f3e305b2397e628e0478da8f9
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803455"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a>Sommes de contrôle du fichier XOML de workflow passées de MD5 à SHA256

|   |   |
|---|---|
|Détails|Pour prendre en charge le débogage des workflows XOML avec Visual Studio, lorsque des projets de workflow contenant des fichiers XOML sont générés, une somme de contrôle du contenu du fichier XOML est incluse dans le code généré comme une valeur <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType>. Dans .NET Framework 4.7.2 et versions antérieures, le hachage de somme de contrôle utilisait l’algorithme MD5, ce qui entraînait des problèmes sur les systèmes compatibles FIPS. À compter de .NET Framework 4.8, l’algorithme utilisé est SHA256. Pour des raisons de compatibilité avec le WorkflowMarkupSourceAttribute.MD5Digest, seuls les 16 premiers octets de la somme de contrôle générée sont utilisés. Cela peut entraîner des problèmes pendant le débogage. Vous aurez peut-être à regénérer votre projet.|
|Suggestion|Si la regénération de votre projet ne résout pas le problème, essayez de définir le commutateur <code>AppContext</code> &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; sur true. Dans le code, cela donne :<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>Dans un fichier de configuration (qui doit être MSBuild.exe.config pour le MSBuild.exe que vous utilisez), cela donne :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Portée|Mineur|
|Version|4.8|
|Type|Reciblage|

