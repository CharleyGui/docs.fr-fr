---
title: RelativeSource, extension de balisage
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 47117d684a981f31e22cf513fc78e1e2dda73f8a
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141269"
---
# <a name="relativesource-markupextension"></a>RelativeSource, extension de balisage

Spécifie les propriétés <xref:System.Windows.Data.RelativeSource> d’une source de liaison à utiliser dans une [extension de balisage de liaison](binding-markup-extension.md), <xref:System.Windows.Data.Binding.RelativeSource%2A> ou lors de <xref:System.Windows.Data.Binding> la définition de la propriété d’un élément établi en XAML.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" ... />
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a>Utilisation des attributs XAML (imbriqués dans l'extension de liaison)

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" ... />
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
|`modeEnumValue`|Celui-ci peut avoir l'une des valeurs suivantes :<br /><br /> -Le jeton `Self`de chaîne ; correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa <xref:System.Windows.Data.RelativeSource.Mode%2A> propriété définie sur <xref:System.Windows.Data.RelativeSourceMode.Self>.<br />-Le jeton `TemplatedParent`de chaîne ; correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa <xref:System.Windows.Data.RelativeSource.Mode%2A> propriété définie sur <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.<br />-Le jeton `PreviousData`de chaîne ; correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa <xref:System.Windows.Data.RelativeSource.Mode%2A> propriété définie sur <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.<br />-Voir ci-dessous pour `FindAncestor` plus d’informations sur le mode.|
|`FindAncestor`|Le jeton de chaîne `FindAncestor`. L'utilisation de ce jeton accède à un mode dans lequel un `RelativeSource` spécifie un type d'ancêtre et, en option, un niveau d'ancêtre. Ce correspond à un <xref:System.Windows.Data.RelativeSource> comme créé avec sa propriété <xref:System.Windows.Data.RelativeSource.Mode%2A> définie à <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.|
|`typeName`|Nécessaire pour le mode `FindAncestor`. Le nom d'un type, qui remplit la propriété <xref:System.Windows.Data.RelativeSource.AncestorType%2A>.|
|`intLevel`|Facultatif pour le mode `FindAncestor`. Un niveau d'ancêtre (évalué vers la direction du parent dans l'arborescence logique).|

## <a name="remarks"></a>Notes 

`{RelativeSource TemplatedParent}`les utilisations de liaison sont une technique clé qui résout un plus grand concept de séparation de l’interface utilisateur d’un contrôle et d’une logique de contrôle. Cela permet la liaison à partir de la définition de modèle au parent basé sur des modèles (instance de l'objet à l'exécution où le modèle est appliqué). Dans ce cas, l' [extension de balisage TemplateBinding](templatebinding-markup-extension.md) est en fait un raccourci pour l’expression de `{Binding RelativeSource={RelativeSource TemplatedParent}}`liaison suivante :. `TemplateBinding`les `{RelativeSource TemplatedParent}` utilisations ou sont toutes deux uniquement pertinentes dans le code XAML qui définit un modèle. Pour plus d’informations, consultez l' [extension de balisage TemplateBinding](templatebinding-markup-extension.md).

`{RelativeSource FindAncestor}`est principalement utilisé dans les modèles de contrôle ou les compositions d’interface utilisateur autonomes prévisibles, pour les cas où un contrôle est toujours supposé être dans une arborescence d’éléments visuels d’un certain type d’ancêtre. Par exemple, les éléments d'un contrôle d'éléments peuvent utiliser des utilisations de `FindAncestor` pour les lier aux propriétés de leur ancêtre parent du contrôle d'éléments. Ou les éléments qui font partie de la composition de contrôle dans un modèle peuvent utiliser des liaisons de `FindAncestor` aux éléments parents dans cette même structure de composition.

Dans la syntaxe d'élément objet du mode `FindAncestor` indiqué dans les sections de syntaxe XAML, la deuxième syntaxe d'élément objet est utilisée spécifiquement pour le mode `FindAncestor`. Le mode `FindAncestor` requiert une valeur <xref:System.Windows.Data.RelativeSource.AncestorType%2A>. Vous devez définir <xref:System.Windows.Data.RelativeSource.AncestorType%2A> en tant qu’attribut à l’aide d’une référence d' [extension de balisage x :type](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) au type d’ancêtre à rechercher. La valeur <xref:System.Windows.Data.RelativeSource.AncestorType%2A> est utilisée lorsque la demande de liaison est traitée lors de l'exécution.

Pour le mode `FindAncestor`, la propriété <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> facultative peut contribuer à désambiguïser la recherche d'ancêtre dans les cas où il existe peut-être plusieurs ancêtres de ce type présents dans l'arborescence d'éléments.

Pour plus d'informations sur l'utilisation du mode `FindAncestor`, consultez <xref:System.Windows.Data.RelativeSource>.

`{RelativeSource Self}`est utile pour les scénarios où une propriété d’une instance doit dépendre de la valeur d’une autre propriété de la même instance, et qu’aucune relation de propriété de dépendance générale (telle que la contrainte) n’existe déjà entre ces deux propriétés. Bien qu’il soit rare que deux propriétés existent sur un objet de telle sorte que les valeurs soient littéralement identiques (et sont de type identique), vous pouvez `Converter` également appliquer un paramètre à une `{RelativeSource Self}`liaison qui a, et utiliser le convertisseur pour effectuer une conversion entre des types source et cible. Un autre scénario `{RelativeSource Self}` pour est dans le cadre <xref:System.Windows.MultiDataTrigger>d’un.

Par exemple, le code XAML suivant définit un élément <xref:System.Windows.Shapes.Rectangle> tels que tout ce que la valeur est entrée pour <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> est toujours angle droit : `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`

`{RelativeSource PreviousData}`est utile dans les modèles de données ou dans les cas où des liaisons utilisent une collection comme source de données. Vous pouvez utiliser `{RelativeSource PreviousData}` pour mettre en surbrillance les relations entre des éléments de données adjacents dans la collection. Une technique connexe est de générer <xref:System.Windows.Data.MultiBinding> entre des éléments actuels et précédents dans la source de données, et d'utiliser un convertisseur sur cette liaison pour déterminer la différence entre les deux éléments et leurs propriétés.

Dans l'exemple suivant, le premier <xref:System.Windows.Controls.TextBlock> dans le modèle d'éléments affiche le numéro actuel. La deuxième <xref:System.Windows.Controls.TextBlock> liaison est un <xref:System.Windows.Data.MultiBinding> qui a nominalement deux <xref:System.Windows.Data.Binding> constituants : l’enregistrement actif et une liaison qui utilise délibérément l’enregistrement de données précédent `{RelativeSource PreviousData}`à l’aide de. Ensuite, un convertisseur sur <xref:System.Windows.Data.MultiBinding> calcule la différence et la retourne à la liaison.

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
</ListBox>
```

La description de la liaison de données comme concept n’est pas abordée ici, consultez [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données.

Dans l' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentation du processeur XAML, la gestion de cette extension de balisage est <xref:System.Windows.Data.RelativeSource> définie par la classe.

`RelativeSource` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage en `{` XAML `}` utilisent les caractères et dans leur syntaxe d’attribut, qui est la Convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.Binding>
- [Application d'un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d’ensemble des déclarations de liaison](../data/binding-declarations-overview.md)
- [x:Type, extension de balisage](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
