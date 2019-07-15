---
ms.openlocfilehash: d3d336b9626437d8fb597de421005763afd5f021
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859328"
---
### <a name="changes-in-path-normalization"></a>Changements dans la normalisation des chemins

|   |   |
|---|---|
|Détails|À partir des applications qui ciblent .NET Framework 4.6.2, la façon dont le runtime normalise les chemins a changé. La normalisation d’un chemin implique la modification de la chaîne qui identifie un chemin ou un fichier afin qu’elle soit conforme à un chemin valide sur le système d’exploitation cible. La normalisation implique généralement :<ul><li>La mise en forme canonique des composants et séparateurs de répertoires.</li><li>L’application du répertoire actuel à un chemin d’accès relatif.</li><li>L’évaluation du répertoire relatif (.) ou du répertoire parent (..) dans un chemin.</li><li>La suppression des caractères spécifiés.</li></ul>À partir des applications qui ciblent .NET Framework 4.6.2, les changements suivants apportés à la normalisation des chemins sont activés par défaut :<ul><li>Le runtime défère à la fonction [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) du système d’exploitation pour normaliser les chemins d’accès.</li><li>La normalisation n’implique plus la suppression de la fin des segments de répertoire (comme un espace à la fin d’un nom de répertoire).</li><li>Prise en charge de la syntaxe de chemin d’appareil en mode confiance totale, notamment <code>\\.\</code> and, for file I/O APIs in mscorlib.dll, <code>\\?\</code>.</li><li>The runtime does not validate device syntax paths.</li><li>The use of device syntax to access alternate data streams is supported.</li></ul>These changes improve performance while allowing methods to access previously inaccessible paths. Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.|
|Suggestion|Les applications qui ciblent .NET Framework 4.6.2 ou une version ultérieure peuvent refuser ce changement et utiliser la normalisation héritée en ajoutant le code suivant à la section <code>&lt;runtime&gt;</code> du fichier de configuration d’application :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Les applications qui ciblent .NET Framework 4.6.1 ou une version antérieure mais qui s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure peuvent activer les changements apportées à la normalisation des chemins en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier de configuration d’application :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Portée|Mineur|
|Version|4.6.2|
|Type|Reciblage|

