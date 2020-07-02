---
ms.openlocfilehash: 04c4fb4c8e9da8c58a5e26f78a7b13aa6a0df4a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614462"
---
### <a name="changes-in-path-normalization"></a>Changements dans la normalisation des chemins

#### <a name="details"></a>Détails

À partir des applications qui ciblent .NET Framework 4.6.2, la façon dont le runtime normalise les chemins a changé. La normalisation d’un chemin implique la modification de la chaîne qui identifie un chemin ou un fichier afin qu’elle soit conforme à un chemin valide sur le système d’exploitation cible. La normalisation implique généralement :

- La mise en forme canonique des composants et séparateurs de répertoires.
- L’application du répertoire actuel à un chemin d’accès relatif.
- L’évaluation du répertoire relatif (.) ou du répertoire parent (..) dans un chemin.
- La suppression des caractères spécifiés.
À partir des applications qui ciblent .NET Framework 4.6.2, les changements suivants apportés à la normalisation des chemins sont activés par défaut :
  - Le runtime défère à la fonction [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) du système d’exploitation pour normaliser les chemins d’accès.
- La normalisation n’implique plus la suppression de la fin des segments de répertoire (comme un espace à la fin d’un nom de répertoire).
- Prise en charge de la syntaxe du chemin d’appareil avec une confiance totale, y compris `\\.\` et, pour les API d’E/S de fichiers dans mscorlib.dll, `\\?\`.
- Le runtime ne valide pas les chemins d’accès de syntaxe de périphérique.
- L’utilisation de la syntaxe de périphérique pour accéder aux autres flux de données est prise en charge.
Ces modifications améliorent les performances tout en permettant aux méthodes d’accéder à des chemins auparavant inaccessibles. Les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures, mais s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure ne sont pas concernées par ce changement.

#### <a name="suggestion"></a>Suggestion

Les applications qui ciblent .NET Framework 4.6.2 ou une version ultérieure peuvent refuser ce changement et utiliser la normalisation héritée en ajoutant le code suivant à la section `<runtime>` du fichier de configuration d’application :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>
```

Les applications qui ciblent .NET Framework 4.6.1 ou une version antérieure mais qui s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure peuvent activer les changements apportées à la normalisation des chemins en ajoutant la ligne suivante à la section `<runtime>` du fichier de configuration d’application :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.6.2       |
| Type    | Reciblage |
