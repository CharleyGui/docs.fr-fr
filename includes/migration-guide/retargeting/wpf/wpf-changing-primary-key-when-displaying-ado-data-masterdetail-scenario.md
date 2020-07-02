---
ms.openlocfilehash: 35fc4782ebbba33f5fc6668712af9d89d00cafe9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614619"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a>WPF : Modification d’une clé primaire lors de l’affichage de données ADO dans un scénario maître/détail

#### <a name="details"></a>Détails

Supposez que vous avez une collection ADO d’éléments de type `Order` avec une relation nommée &quot;OrderDetails&quot; mise en relation avec une collection d’éléments de type `Detail` via la clé primaire &quot;OrderID&quot;. Dans votre application WPF, vous pouvez lier un contrôle de liste aux détails d’un ordre spécifique :

```xaml
<ListBox ItemsSource="{Binding Path=OrderDetails}" >
```

où DataContext est un `Order`. WPF obtient la valeur de la `OrderDetails` propriété : une collection D de tous les `Detail` éléments dont `OrderID` la correspond à la valeur `OrderID` de l’élément maître. Le changement de comportement se produit lorsque vous modifiez la clé primaire `OrderID` de l’élément maître. ADO modifie automatiquement le `OrderID` de chacun des enregistrements concernés dans la collection de détails (à savoir les enregistrements copiés dans la collection D).  Qu'advient-il ensuite de la collection D ?

- Ancien comportement : la collection D est effacée. L’élément principal ne déclenche *aucune* notification de modification pour la propriété `OrderDetails`. La zone de liste continue d’utiliser la collection D, qui est maintenant vide.
- Nouveau comportement : la collection D reste inchangée. Chacun de ses éléments déclenche une notification de modification pour la propriété `OrderID`. La zone de liste continue d’utiliser la collection D et affiche les détails avec le nouveau `OrderID`. WPF implémente le nouveau comportement en créant la collection D d’une autre manière : en appelant la méthode ADO <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> avec l’argument `followParent` défini sur `true`.

#### <a name="suggestion"></a>Suggestion

Une application obtient le nouveau comportement à l’aide du commutateur AppContext suivant.

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false"/>
  </runtime>
</configuration>
```

Le commutateur par défaut est `true` (ancien comportement) pour les applications qui ciblent .NET 4.7.1 ou version antérieure, et `false` (nouveau comportement) pour les applications qui ciblent .NET 4.7.2 ou version ultérieure.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.7.2       |
| Type    | Reciblage |
