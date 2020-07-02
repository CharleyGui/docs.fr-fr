---
ms.openlocfilehash: 67e3ff5000ebd38064ed8a57e4fe561afa31f8d8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614478"
---
### <a name="long-path-support"></a>Prise en charge des chemins d’accès longs

#### <a name="details"></a>Détails

À partir des applications qui ciblent .NET Framework 4.6.2, les chemins longs (comprenant jusqu’à 32 000 caractères) sont pris en charge et la limite de 260 caractères (ou `MAX_PATH`) sur la longueur du chemin est supprimée. Pour les applications qui sont recompilées pour cibler .NET Framework 4.6.2, les chemins de code qui levaient précédemment un <xref:System.IO.PathTooLongException?displayProperty=fullName> car un chemin dépassait 260 caractères lèvent désormais un <xref:System.IO.PathTooLongException?displayProperty=fullName> uniquement quand les conditions suivantes sont remplies :

- La longueur du chemin est supérieure à <xref:System.Int16.MaxValue> (32 767) caractères.
- Le système d’exploitation renvoie `COR_E_PATHTOOLONG` ou son équivalent.
Pour les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures, le runtime levait automatiquement un <xref:System.IO.PathTooLongException?displayProperty=fullName> chaque fois qu’un chemin comportait plus de 260 caractères.

#### <a name="suggestion"></a>Suggestion

Pour les applications qui ciblent .NET Framework 4.6.2, vous pouvez refuser la prise en charge des chemins longs en ajoutant le code suivant à la section `<runtime>` de votre fichier `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />
</runtime>
```

Pour les applications qui ciblent des versions antérieures du .NET Framework mais qui s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure, vous pouvez accepter la prise en charge des chemins longs en ajoutant le code suivant à la section `<runtime>` de votre fichier `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />
</runtime>
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.6.2       |
| Type    | Reciblage |
