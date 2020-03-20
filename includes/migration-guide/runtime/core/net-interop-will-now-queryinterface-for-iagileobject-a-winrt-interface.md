---
ms.openlocfilehash: 0036fc2b03dde64d24d883e55b9f00c931f0c218
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997603"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>.NET Interop effectue désormais un QI pour IAgileObject (interface WinRT)

|   |   |
|---|---|
|Détails|Lorsque vous utilisez un événement WinRT avec un délégué .NET, Windows effectue un QI (QueryInterface) pour IAgileObject à compter de .NET Framework 4.8.  Dans les versions précédentes du .NET Framework, le runtime échouait et l’événement ne pouvait pas être inscrit.<ul><li>[ x ] Quirked</li></ul>|
|Suggestion|Si l’activation de QI pour IAgileObject arrête l’exécution, vous pouvez désactiver ce code en définissant la configuration suivante. <h4>Méthode 1 : Variable de l’environnement</h4> Définissez la variable d’environnement suivante : COMPLUS_DisableCCWSupportIAgileObject=1 Cette méthode affecte tout environnement héritant de cette variable d’environnement. Il peut s’agir d’une seule session de console, ou cela pourrait affecter l’ensemble de la machine si vous définissez la variable d’environnement à l’échelle mondiale. Le nom variable de l’environnement n’est pas sensible aux cas. <h4>Méthode 2 : Registre</h4> À l’aide de Registry Editor (regedit.exe), trouvez l’un des sous-clés suivants : HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft.NETFramework HKEY_CURRENT_USER-SOFTWARE-Microsoft.NETFrameworkThen ajouter le nom suivant : Nom de la valeur : DisableCCWSupportIAgileObject Type: DWORD (32 bits) Valeur (également appelée REG_WORD) Valeur: 1Vous pouvez utiliser le Windows REG. OUTIL EXE pour ajouter cette valeur à partir d’un environnement de commande ou de script. Par exemple :<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>Dans ce cas, <code>HKLM</code> peut être utilisé à la place de <code>HKEY_LOCAL_MACHINE</code>. Utilisez <code>reg add /?</code> pour voir de l’aide sur cette syntaxe. Le nom de valeur du registre n’est pas sensible aux cas.|
|Étendue|Edge|
|Version|4.8|
|Type|Runtime|
