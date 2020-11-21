---
description: '#Nullable-référence C#'
title: '#Nullable-référence C#'
ms.date: 11/18/2020
f1_keywords:
- '#nullable'
helpviewer_keywords:
- '#nullable directive [C#]'
ms.openlocfilehash: 4c114a09f29769fcc824bcdabdc1d523e33f199d
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099462"
---
# <a name="nullable-c-reference"></a>#nullable (référence C#)

La `#nullable` directive de préprocesseur définit le contexte d' *annotation Nullable* et le *contexte d’avertissement Nullable*. Cette directive contrôle si les annotations Nullable ont un effet et si des avertissements de possibilité de valeur NULL sont fournis. Chaque contexte est *désactivé* ou *activé*.

Les deux contextes peuvent être spécifiés au niveau du projet (en dehors du code source C#). La `#nullable` directive contrôle les contextes d’annotation et d’avertissement et est prioritaire sur les paramètres au niveau du projet. Une directive définit le ou les contexte (s) qu’elle contrôle jusqu’à ce qu’une autre directive la remplace, ou jusqu’à la fin du fichier source.

L’effet des directives est le suivant :

- `#nullable disable`: Définit l’annotation Nullable et les contextes d’avertissement sur *désactivé*.
- `#nullable enable`: Définit l’annotation Nullable et les contextes d’avertissement sur *activé*.
- `#nullable restore`: Restaure l’annotation Nullable et les contextes d’avertissement dans les paramètres du projet.
- `#nullable disable annotations`: Définit le contexte d’annotation Nullable sur *désactivé*.
- `#nullable enable annotations`: Définit le contexte d’annotation Nullable sur *activé*.
- `#nullable restore annotations`: Restaure le contexte d’annotation Nullable aux paramètres du projet.
- `#nullable disable warnings`: Définit le contexte d’avertissement Nullable sur *désactivé*.
- `#nullable enable warnings`: Définit le contexte d’avertissement Nullable sur *activé*.
- `#nullable restore warnings`: Restaure le contexte d’avertissement Nullable aux paramètres du projet.

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur C#](./index.md)
