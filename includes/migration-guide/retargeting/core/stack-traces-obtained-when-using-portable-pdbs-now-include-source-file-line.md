---
ms.openlocfilehash: c7500550cd9714a9788a7dea68af04823f000f7f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614533"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>Les traces obtenues durant l’utilisation de fichiers PDB portables incluent désormais les informations sur les lignes et les fichiers sources, si elles sont demandées

#### <a name="details"></a>Détails

À compter de .NET Framework 4.7.2, les traces obtenues durant l’utilisation de fichiers PDB portables incluent les informations sur les lignes et les fichiers sources quand elles sont demandées. Dans les versions antérieures de .NET Framework 4.7.2, les informations sur les lignes et les fichiers sources n’étaient pas disponibles pendant l’utilisation de fichiers PDB portables même si elles étaient explicitement demandées.

#### <a name="suggestion"></a>Suggestion

Pour les applications qui ciblent .NET Framework 4.7.2, vous pouvez refuser les informations sur les lignes et les fichiers sources durant l’utilisation de fichiers PDB portables en ajoutant le code suivant à la section `<runtime>` de votre fichier `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true" />
</runtime>
```

Pour les applications qui ciblent des versions antérieures de .NET Framework mais qui s’exécutent sur .NET Framework 4.7.2 ou une version ultérieure, vous pouvez accepter les informations sur les lignes et les fichiers sources durant l’utilisation de fichiers PDB portables en ajoutant le code suivant à la section `<runtime>` de votre fichier `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false" />
</runtime>
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.7.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)>
