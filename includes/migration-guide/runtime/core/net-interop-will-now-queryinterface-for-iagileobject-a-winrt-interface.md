---
ms.openlocfilehash: 0036fc2b03dde64d24d883e55b9f00c931f0c218
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997603"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>.NET Interop effectue désormais un QI pour IAgileObject (interface WinRT)

|   |   |
|---|---|
|Détails|Lorsque vous utilisez un événement WinRT avec un délégué .NET, Windows effectue un QI (QueryInterface) pour IAgileObject à compter de .NET Framework 4.8.  Dans les versions précédentes du .NET Framework, le runtime échouait et l’événement ne pouvait pas être inscrit.<ul><li>[ x ] Quirked</li></ul>|
|Suggestion|Si l’activation de QI pour IAgileObject arrête l’exécution, vous pouvez désactiver ce code en définissant la configuration suivante. <h4>Méthode 1 : Variable d’environnement</h4> Définissez la variable d’environnement suivante : COMPLUS_DisableCCWSupportIAgileObject=1 Cette méthode affecte tout environnement héritant de cette variable d’environnement. Il peut s’agir d’une seule session de console, ou elle peut affecter l’ordinateur entier si vous définissez la variable d’environnement globalement. Le nom de la variable d’environnement n’est pas sensible à la casse. <h4>Méthode 2 : Registre</h4> Utilisez l’Éditeur du Registre (regedit.exe) pour trouver l’une des sous-clés suivantes : HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFramework. Ensuite, ajoutez le contenu suivant : Value name: DisableCCWSupportIAgileObject Type: DWORD (32-bit) Value (also called REG_WORD) Value: 1 Vous pouvez utiliser l’outil Windows REG.EXE pour ajouter cette valeur à partir d’une ligne de commande ou d’un environnement de script. Par exemple :<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>Dans ce cas, <code>HKLM</code> peut être utilisé à la place de <code>HKEY_LOCAL_MACHINE</code>. Utilisez <code>reg add /?</code> pour afficher de l’aide sur cette syntaxe. Le nom de la valeur de registre ne respecte pas la casse.|
|`Scope`|Microsoft Edge|
|Version|4.8|
|Type|Runtime|
