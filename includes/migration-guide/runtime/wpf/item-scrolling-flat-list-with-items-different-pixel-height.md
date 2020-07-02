---
ms.openlocfilehash: fbf3c0c8f1d11f9f5997a4d1027242c4710c7107
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621790"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Défilement des éléments d’une liste plate avec des éléments de différentes hauteurs en pixels

#### <a name="details"></a>Détails

Quand un <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> affiche une collection avec la virtualisation (<code>IsVirtualizing=true</code>) et le défilement d’éléments (<code>ScrollUnit=Item</code>), et quand le contrôle fait défiler pour afficher un élément dont la hauteur en pixels diffère de celle de ses voisins, le <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> effectue une itération sur tous les éléments de la collection. L’interface utilisateur ne répond pas pendant cette itération ; Si la collection est volumineuse, cela peut être perçu comme un blocage. L’itération se produit dans d’autres circonstances, même dans les versions précédentes de .NET Framework. Par exemple, elle se produit lors du défilement de pixels (<code>ScrollUnit=Pixel</code>) quand un élément avec une hauteur en pixels différente est rencontré et lors du défilement d’éléments de données hiérarchiques (comme dans un <xref:System.Windows.Controls.TreeView?displayProperty=fullName> ou un <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> avec le regroupement activé) quand un élément avec un nombre d’éléments descendants différent de celui de ses voisins est rencontré. Pour le cas du défilement d’éléments et d’une hauteur en pixels différente, l’itération a été introduite dans le .NET Framework 4.6.1 pour corriger des bogues dans la présentation des données hiérarchiques.  Elle n’est pas nécessaire si les données sont plates (pas de hiérarchie) et .NET Framework 4.6.2 ne l’effectue donc pas dans ce cas.

#### <a name="suggestion"></a>Suggestion

Si l’itération se produit dans .NET Framework 4.6.1 mais pas dans les versions antérieures, c’est-à-dire si <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> effectue le défilement d’éléments d’une liste plate comportant des éléments avec des hauteurs en pixels différentes, vous avez deux solutions :<ol><li>Installer .NET Framework 4.6.2</li><li>Installer le correctif HR 1605 pour .NET Framework 4.6.1</li></ol>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6.1|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
