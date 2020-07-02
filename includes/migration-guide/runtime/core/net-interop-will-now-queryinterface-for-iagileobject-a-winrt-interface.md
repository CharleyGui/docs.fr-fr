---
ms.openlocfilehash: 150b94b55fa8f2a29f1da7cf7ac7bf6dd06b9666
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621979"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>.NET Interop effectue désormais un QI pour IAgileObject (interface WinRT)

#### <a name="details"></a>Détails

Lorsque vous utilisez un événement WinRT avec un délégué .NET, Windows effectue un QI (QueryInterface) pour IAgileObject à compter de .NET Framework 4.8.  Dans les versions précédentes du .NET Framework, le runtime échouait et l’événement ne pouvait pas être inscrit.<ul><li>[ x ] Quirked</li></ul>

#### <a name="suggestion"></a>Suggestion

Si l’activation de QI pour IAgileObject arrête l’exécution, vous pouvez désactiver ce code en définissant la configuration suivante. <h4>Méthode 1 : variable d’environnement</h4> Définissez la variable d’environnement suivante : COMPLUS_DisableCCWSupportIAgileObject=1 Cette méthode affecte tout environnement héritant de cette variable d’environnement. Il peut s’agir d’une seule session de console, ou elle peut affecter l’ordinateur entier si vous définissez la variable d’environnement globalement. Le nom de la variable d’environnement n’est pas sensible à la casse. <h4>Méthode 2 : Registre</h4> À l’aide de l’éditeur du Registre (regedit.exe), recherchez l’une des sous-clés suivantes : HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER \SOFTWARE\Microsoft.NETFrameworkThen ajoutez la valeur suivante : nom de la valeur : DisableCCWSupportIAgileObject type : DWORD (32-bit) value (également appelée REG_WORD) value : 1Vous pouvez utiliser l’outil de REG.EXE Windows pour ajouter cette valeur à partir d’un environnement de ligne de commande ou de script. Par exemple :<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>Dans ce cas, <code>HKLM</code> peut être utilisé à la place de <code>HKEY_LOCAL_MACHINE</code>. Utilisez <code>reg add /?</code> pour afficher de l’aide sur cette syntaxe. Le nom de la valeur de registre ne respecte pas la casse.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.8|
|Type|Runtime|
