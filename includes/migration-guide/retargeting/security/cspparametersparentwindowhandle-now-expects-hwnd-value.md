---
ms.openlocfilehash: 72f907c117748fb19ca0663f24445a8c978afd32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235530"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters.ParentWindowHandle attend maintenant une valeur HWND

|   |   |
|---|---|
|Détails|La valeur <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle>, introduite dans .NET Framework 2.0, permet à une application d’inscrire une valeur de handle de fenêtre parente, pour que toute interface utilisateur nécessaire pour accéder à la clé (par exemple, une invite de code confidentiel ou une boîte de dialogue de consentement) s’ouvre sous la forme d’un enfant modal de la fenêtre spécifiée. À partir des applications qui ciblent .NET Framework 4.7, une application Windows Forms peut définir la propriété <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> avec du code semblable au suivant :<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>Dans les versions précédentes du .NET Framework, la valeur devait être un <xref:System.IntPtr?displayProperty=name> représentant un emplacement en mémoire où se trouvait la valeur [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND). La définition de la propriété sur form.Handle sur Windows 7 et les versions antérieures n’avait aucun effet, mais sur Windows 8 et les versions ultérieures, cela entraîne un &quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=name> : Le paramètre est incorrect.&quot;|
|Suggestion|Les applications ciblant .NET Framework 4.7 ou ultérieur qui souhaitent inscrire une relation de fenêtre parente sont encouragées à utiliser la forme simplifiée :<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>Les utilisateurs qui avaient identifié que la bonne valeur à passer était l’adresse d’un emplacement de la mémoire qui détenait la valeur <code>form.Handle</code> peuvent refuser ce changement de comportement en définissant le commutateur AppContext <code>Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle</code> sur <code>true</code> :<ol><li>En définissant des commutateurs de compatibilité programmatiquement sur AppContext, comme expliqué [ici](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>En ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier app.config :</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>À l’inverse, les utilisateurs qui souhaitent adopter ce nouveau comportement sur le runtime .NET Framework 4.7 quand l’application se charge sur des versions antérieures du .NET Framework peuvent définir le commutateur AppContext sur <code>false</code>.|
|Étendue|Secondaire|
|Version|4,7|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType></li></ul>|
