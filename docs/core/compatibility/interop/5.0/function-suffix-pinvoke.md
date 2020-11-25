---
title: 'Modification avec rupture : aucune détection de suffixe/W sur les plateformes non-Windows'
description: Découvrez les modifications avec rupture d’interopérabilité dans .NET 5,0 où les suffixes ne sont plus ajoutés aux noms d’exportation de fonction lors de la détection des P/Invoke sur les plateformes non-Windows.
ms.date: 08/13/2020
ms.openlocfilehash: a4c612a81796faf80fa257df21232a54f7b95431
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761057"
---
# <a name="no-aw-suffix-probing-on-non-windows-platforms"></a>Pas de détection de suffixe A/W sur les plateformes non-Windows

Les runtimes .NET n’ajoutent plus `A` `W` de suffixe ou pour les noms d’exportation de fonction lors de la détection pour P/Invoke sur les plateformes non-Windows.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="change-description"></a>Description de la modification

[Windows a une convention](/windows/win32/intl/conventions-for-function-prototypes) d’ajout d' `A` un `W` suffixe ou à SDK Windows noms de fonction, qui correspondent respectivement à la page de codes Windows et aux versions Unicode.

Dans les versions précédentes de .NET, les runtimes CoreCLR et mono ajoutaient `A` un `W` suffixe ou au nom de l’exportation lors de la détection d’exportation pour P/Invoke *sur toutes les plateformes*.

Dans .NET 5,0 et versions ultérieures, `A` un `W` suffixe ou est ajouté au nom d’exportation lors de la découverte de l’exportation *sur Windows uniquement*. Sur les plateformes UNIX, le suffixe n’est pas ajouté. La sémantique des deux runtimes sur la plate-forme Windows reste inchangée.

## <a name="reason-for-change"></a>Motif de modification

Cette modification a été apportée pour simplifier la détection inter-plateformes. La surcharge ne doit pas être encourue, étant donné que les plateformes non-Windows ne contiennent pas cette sémantique.

## <a name="recommended-action"></a>Action recommandée

Pour atténuer la modification, vous pouvez ajouter manuellement le suffixe souhaité sur les plateformes non-Windows. Par exemple :

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

## <a name="affected-apis"></a>API affectées

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

### Category

Interop

-->
