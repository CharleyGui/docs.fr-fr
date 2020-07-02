---
ms.openlocfilehash: a3ba42868577ac20ea2e082f90fc4973a1bfe108
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622350"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a>L’arrière-plan de RibbonGroup est défini sur Transparent dans les versions localisées

#### <a name="details"></a>Détails

L’arrière-plan de <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> sur les versions localisées était toujours dessiné avec le pinceau Transparent, ce qui offrait une expérience assez pauvre de l’interface utilisateur. Ce point est résolu dans le correctif de .NET Framework 4.7 WPF par le biais d’une mise à jour des ressources localisées pour <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, qui à son tour garantit que le bon pinceau est sélectionné.

#### <a name="suggestion"></a>Suggestion

Mettre à niveau vers .NET Framework 4.7

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6.2|
|Type|Runtime|
