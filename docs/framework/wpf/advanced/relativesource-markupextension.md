---
title: RelativeSource, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 6301299da966ade9b5cc7ccd105c8269a486744e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646224"
---
# <a name="relativesource-markupextension"></a>RelativeSource, extension de balisage

Spécifie <xref:System.Windows.Data.RelativeSource> les propriétés d’une source contraignante, à <xref:System.Windows.Data.Binding.RelativeSource%2A> utiliser dans <xref:System.Windows.Data.Binding> le cadre [d’une extension de balisage contraignante,](binding-markup-extension.md)ou lors de la mise en place de la propriété d’un élément établi dans XAML.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>Utilisation des attributs XAML (imbriqués dans l'extension de liaison)

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>
```

## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

-ou-

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource
      Mode="FindAncestor"
      AncestorType="{x:Type typeName}"
      AncestorLevel="intLevel"
    />
  </Binding.RelativeSource>
</Binding>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`modeEnumValue`|Celui-ci peut avoir l'une des valeurs suivantes :<br /><br /> - Le jeton `Self`de cordes ; correspond à <xref:System.Windows.Data.RelativeSource> un tel <xref:System.Windows.Data.RelativeSource.Mode%2A> qu’il <xref:System.Windows.Data.RelativeSourceMode.Self>a été créé avec sa propriété fixée à .<br />- Le jeton `TemplatedParent`de cordes ; correspond à <xref:System.Windows.Data.RelativeSource> un tel <xref:System.Windows.Data.RelativeSource.Mode%2A> qu’il <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>a été créé avec sa propriété fixée à .<br />- Le jeton `PreviousData`de cordes ; correspond à <xref:System.Windows.Data.RelativeSource> un tel <xref:System.Windows.Data.RelativeSource.Mode%2A> qu’il <xref:System.Windows.Data.RelativeSourceMode.PreviousData>a été créé avec sa propriété fixée à .<br />- Voir ci-dessous pour plus d’informations sur `FindAncestor` le mode.|
|`FindAncestor`|Le jeton de chaîne `FindAncestor`. L'utilisation de ce jeton accède à un mode dans lequel un `RelativeSource` spécifie un type d'ancêtre et, en option, un niveau d'ancêtre. Ce correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa propriété <xref:System.Windows.Data.RelativeSource.Mode%2A> définie à <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.|
|`typeName`|Nécessaire pour le mode `FindAncestor`. Le nom d'un type, qui remplit la propriété <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.|
|`intLevel`|Facultatif pour le mode `FindAncestor`. Un niveau d'ancêtre (évalué vers la direction du parent dans l'arborescence logique).|

## <a name="remarks"></a>Notes

`{RelativeSource TemplatedParent}`les utilisations de liaison sont une technique clé qui aborde un concept plus large de la séparation de l’interface utilisateur d’un contrôle et de la logique d’un contrôle. Cela permet la liaison à partir de la définition de modèle au parent basé sur des modèles (instance de l'objet à l'exécution où le modèle est appliqué). Pour ce cas, [l’extension de markup TemplateBinding](templatebinding-markup-extension.md) est en `{Binding RelativeSource={RelativeSource TemplatedParent}}`fait un raccourci pour l’expression contraignante suivante: . `TemplateBinding`ou `{RelativeSource TemplatedParent}` les utilisations ne sont pertinentes que dans le XAML qui définit un modèle. Pour plus d’informations, voir [TemplateBinding Markup Extension](templatebinding-markup-extension.md).

`{RelativeSource FindAncestor}`est principalement utilisé dans les modèles de contrôle ou les compositions prévisibles d’interface utilisateur autonome, pour les cas où un contrôle est toujours prévu d’être dans un arbre visuel d’un certain type d’ancêtre. Par exemple, les éléments d'un contrôle d'éléments peuvent utiliser des utilisations de `FindAncestor` pour les lier aux propriétés de leur ancêtre parent du contrôle d'éléments. Ou les éléments qui font partie de la composition de contrôle dans un modèle peuvent utiliser des liaisons de `FindAncestor` aux éléments parents dans cette même structure de composition.

Dans la syntaxe d'élément objet du mode `FindAncestor` indiqué dans les sections de syntaxe XAML, la deuxième syntaxe d'élément objet est utilisée spécifiquement pour le mode `FindAncestor`. Le mode `FindAncestor` requiert une valeur <xref:System.Windows.Data.RelativeSource.AncestorType%2A>. Vous devez <xref:System.Windows.Data.RelativeSource.AncestorType%2A> définir comme attribut à l’aide d’une référence [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) au type d’ancêtre à rechercher. La valeur <xref:System.Windows.Data.RelativeSource.AncestorType%2A> est utilisée lorsque la demande de liaison est traitée lors de l'exécution.

Pour le mode `FindAncestor`, la propriété <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> facultative peut contribuer à désambiguïser la recherche d'ancêtre dans les cas où il existe peut-être plusieurs ancêtres de ce type présents dans l'arborescence d'éléments.

Pour plus d'informations sur l'utilisation du mode `FindAncestor`, consultez <xref:System.Windows.Data.RelativeSource>.

`{RelativeSource Self}`est utile pour les scénarios où une propriété d’une instance devrait dépendre de la valeur d’une autre propriété d’une même instance, et qu’il n’existe déjà aucune relation de propriété à dépendance générale (comme la coercition) entre ces deux propriétés. Bien qu’il soit rare que deux propriétés existent sur un objet de telle sorte `Converter` que les valeurs `{RelativeSource Self}`sont littéralement identiques (et sont identiques dactylographiées), vous pouvez également appliquer un paramètre à une liaison qui a, et utiliser le convertisseur pour convertir entre les types de source et de cible. Un autre `{RelativeSource Self}` scénario pour <xref:System.Windows.MultiDataTrigger>est dans le cadre d’un .

Par exemple, le code XAML suivant définit un élément <xref:System.Windows.Shapes.Rectangle> tels que tout ce que la valeur est entrée pour <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> est toujours angle droit : `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}`est utile soit dans les modèles de données, soit dans les cas où les liaisons utilisent une collection comme source de données. Vous pouvez `{RelativeSource PreviousData}` utiliser pour mettre en évidence les relations entre les éléments de données adjacents de la collection. Une technique connexe est de générer <xref:System.Windows.Data.MultiBinding> entre des éléments actuels et précédents dans la source de données, et d'utiliser un convertisseur sur cette liaison pour déterminer la différence entre les deux éléments et leurs propriétés.

Dans l'exemple suivant, le premier <xref:System.Windows.Controls.TextBlock> dans le modèle d'éléments affiche le numéro actuel. La <xref:System.Windows.Controls.TextBlock> deuxième liaison <xref:System.Windows.Data.MultiBinding> est celle <xref:System.Windows.Data.Binding> qui compte nominalement deux constituants : le dossier actuel `{RelativeSource PreviousData}`et une liaison qui utilise délibérément le dossier de données précédent en utilisant . Ensuite, un convertisseur sur <xref:System.Windows.Data.MultiBinding> calcule la différence et la retourne à la liaison.

```xml
<ListBox Name="fibolist">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding}"/>
            <TextBlock>, difference = </TextBlock>
                <TextBlock>
                    <TextBlock.Text>
                        <MultiBinding Converter="{StaticResource DiffConverter}">
                            <Binding/>
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>
                        </MultiBinding>
                    </TextBlock.Text>
                </TextBlock>
            </StackPanel>
        </DataTemplate>
    </ListBox.ItemTemplate>
```

Décrire la liaison des données comme un concept n’est pas couvert ici, voir [Aperçu de liaison des données](../../../desktop-wpf/data/data-binding-overview.md).

Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la mise en œuvre du processeur XAML, la manipulation de cette extension de balisage est définie par la <xref:System.Windows.Data.RelativeSource> classe.

`RelativeSource` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage dans XAML utilisent le `{` syntaxe d’attribut, `}` qui est la convention par laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.Binding>
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [Aperçu de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d’ensemble des déclarations de liaison](../data/binding-declarations-overview.md)
- [x:Type, extension de balisage](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
