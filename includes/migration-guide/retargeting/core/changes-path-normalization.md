---
ms.openlocfilehash: 994876457f9745de99be30e567f400f69a0192fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70259788"
---
### <a name="changes-in-path-normalization"></a>Changements dans la normalisation des chemins

|   |   |
|---|---|
|Détails|À partir des applications qui ciblent .NET Framework 4.6.2, la façon dont le runtime normalise les chemins a changé. La normalisation d’un chemin implique la modification de la chaîne qui identifie un chemin ou un fichier afin qu’elle soit conforme à un chemin valide sur le système d’exploitation cible. La normalisation implique généralement :<ul><li>La mise en forme canonique des composants et séparateurs de répertoires.</li><li>L’application du répertoire actuel à un chemin d’accès relatif.</li><li>L’évaluation du répertoire relatif (.) ou du répertoire parent (..) dans un chemin.</li><li>La suppression des caractères spécifiés.</li></ul>À partir des applications qui ciblent .NET Framework 4.6.2, les changements suivants apportés à la normalisation des chemins sont activés par défaut :<ul><li>Le runtime défère à la fonction [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) du système d’exploitation pour normaliser les chemins d’accès.</li><li>La normalisation n’implique plus la suppression de la fin des segments de répertoire (comme un espace à la fin d’un nom de répertoire).</li><li>Prise en charge de la syntaxe du chemin d’appareil avec une confiance totale, y compris `\\.\` et, pour les API d’E/S de fichiers dans mscorlib.dll, `\\?\`.</li><li>Le runtime ne valide pas les chemins d’accès de syntaxe de périphérique.</li><li>L’utilisation de la syntaxe de périphérique pour accéder aux autres flux de données est prise en charge.</li></ul>Ces modifications améliorent les performances tout en permettant aux méthodes d’accéder à des chemins auparavant inaccessibles. Les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures, mais s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure ne sont pas concernées par ce changement.|
|Suggestion|Les applications qui ciblent .NET Framework 4.6.2 ou une version ultérieure peuvent refuser ce changement et utiliser la normalisation héritée en ajoutant le code suivant à la section <code>&lt;runtime&gt;</code> du fichier de configuration d’application :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Les applications qui ciblent .NET Framework 4.6.1 ou une version antérieure mais qui s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure peuvent activer les changements apportées à la normalisation des chemins en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier de configuration d’application :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Étendue|Secondaire|
|Version|4.6.2|
|Type|Reciblage|
