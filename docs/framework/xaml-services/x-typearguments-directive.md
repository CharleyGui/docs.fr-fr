---
title: x:TypeArguments, directive
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: a2a960870d368e57272b3368e69eb38ebbe2ba5d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053717"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments, directive
Passe des arguments de type de restriction d’un générique au constructeur du type générique.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`object`|Déclaration d’élément objet d’un type XAML, qui est stockée par un type CLR générique. Si `object` fait référence à un type XAML qui n’est pas issu de l’espace `object` de noms XAML par défaut, requiert un préfixe pour indiquer l’espace de noms XAML où `object` existe.|  
|`typeString`|Chaîne qui déclare un ou plusieurs noms de types XAML sous forme de chaînes, qui fournit les arguments de type pour le type générique CLR. Consultez la section Notes pour obtenir des remarques supplémentaires sur la syntaxe.|  
  
## <a name="remarks"></a>Notes  
 Dans la plupart des cas, les types XAML qui sont utilisés comme élément d’information `typeString` dans une chaîne sont préfixés. Les types typiques de contraintes génériques CLR (par exemple <xref:System.Int32> , <xref:System.String>et) proviennent des bibliothèques de classes de base CLR. Ces bibliothèques ne sont pas mappées à des espaces de noms XAML par défaut propres à un Framework standard, et par conséquent requièrent un mappage de préfixe pour l’utilisation de XAML.  
  
 Vous pouvez spécifier plusieurs noms de type XAML à l’aide d’un délimiteur de virgule.  
  
 Si les contraintes génériques elles-mêmes utilisent des types génériques, les arguments de type de contrainte imbriquée peuvent être contenus entre parenthèses ().  
  
 Notez que cette définition de `x:TypeArguments` est spécifique à .NET Framework les services XAML et à l’utilisation du stockage CLR. Une définition au niveau du langage est disponible dans [ \[la section MS\] -XAML 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="usage-examples"></a>Exemples d’utilisation  
 Pour ces exemples, supposez que les définitions d’espace de noms XAML suivantes sont déclarées :  
  
```xaml  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>>\<De la chaîne de liste  
 `<scg:List x:TypeArguments="sys:String" ...>`instancie un nouveau <xref:System.Collections.Generic.List%601> avec un <xref:System.String> argument de type.  
  
### <a name="dictionarystringstring"></a>Chaîne\<de dictionnaire, chaîne >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`instancie un nouveau <xref:System.Collections.Generic.Dictionary%602> avec deux <xref:System.String> arguments de type.  
  
### <a name="queuekeyvaluepairstringstring"></a>Queue < chaîne\<KeyValuePair, String > >  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`instancie un nouveau <xref:System.Collections.Generic.Queue%601> qui a une contrainte de <xref:System.Collections.Generic.KeyValuePair%602> avec les arguments <xref:System.String> de type de contrainte <xref:System.String>interne et.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 et utilisations XAML génériques WPF  
 Pour l’utilisation de XAML 2006 et XAML utilisé pour les applications WPF, les restrictions suivantes existent pour `x:TypeArguments` et les utilisations de type générique à partir de XAML en général :  
  
- Seul l’élément racine d’un fichier XAML peut prendre en charge une utilisation générique XAML qui référence un type générique.  
  
- L’élément racine doit être mappé à un type générique avec au moins un argument de type. Par exemple <xref:System.Windows.Navigation.PageFunction%601>. Les fonctions de page sont le scénario principal pour la prise en charge de l’utilisation générique XAML dans WPF.  
  
- L’élément racine de l’élément objet XAML pour le générique doit également déclarer une classe `x:Class`partielle à l’aide de. Cela est vrai même si vous définissez une action de génération WPF.  
  
- `x:TypeArguments`Impossible de référencer des contraintes génériques imbriquées.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 ou XAML 2006 sans dépendance WPF 3,0 ou 3,5 WPF  
 Dans .NET Framework les services XAML pour XAML 2006 ou XAML 2009, les restrictions liées à WPF sur l’utilisation de XAML générique sont assouplies. Vous pouvez instancier un élément objet générique à n’importe quelle position dans le balisage XAML que le système de type de stockage et le modèle objet peuvent prendre en charge.  
  
 Si vous utilisez XAML 2009 au lieu de mapper les types de base CLR pour obtenir des types XAML pour les primitives de langage courantes, vous pouvez utiliser [des types intégrés pour les primitives de langage XAML courantes](built-in-types-for-common-xaml-language-primitives.md) comme éléments d’information dans un `typeString`. Par exemple, vous pouvez déclarer ce qui suit (les mappages de préfixe ne sont pas affichés, mais x est l’espace de noms XAML du langage XAML pour XAML 2009) :  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 Dans WPF et lorsque vous ciblez .NET Framework 4, vous pouvez utiliser les fonctionnalités XAML `x:TypeArguments` 2009 avec, mais uniquement pour le XAML libre (XAML qui n’est pas compilé par balisage). Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009. Si vous devez compiler le code XAML, vous devez utiliser les restrictions indiquées dans la section « XAML 2006 et les utilisations XAML génériques WPF ».  
  
## <a name="see-also"></a>Voir aussi

- [x:Class, directive](x-class-directive.md)
- [x:Type, extension de balisage](x-type-markup-extension.md)
- [Types intégrés pour les primitives associées au langage XAML courant](built-in-types-for-common-xaml-language-primitives.md)
- [Génériques en XAML](generics-in-xaml.md)
