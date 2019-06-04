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
ms.openlocfilehash: 41f29673622fa7918238dd014b97ee3cf0766257
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486212"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments, directive
Passes contraindre les arguments d’un générique au constructeur du type générique de type.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`object`|Une déclaration d’élément objet d’un type XAML, qui repose sur un type générique du CLR. Si `object` fait référence à un type XAML qui n’est pas à partir de l’espace de noms XAML par défaut, `object` nécessite un préfixe pour indiquer l’espace de noms XAML où `object` existe.|  
|`typeString`|Chaîne qui déclare le XAML d’un ou plusieurs noms de type sous forme de chaînes, qui fournit les arguments de type pour le type générique du CLR. Consultez la section Notes pour accéder aux notes de la syntaxe supplémentaire.|  
  
## <a name="remarks"></a>Notes  
 Dans la plupart des cas, les types XAML qui sont utilisés comme un élément d’information dans un `typeString` chaîne sont préfixés. Les types classiques de contraintes génériques CLR (par exemple, <xref:System.Int32> et <xref:System.String>) proviennent de bibliothèques de classe de base CLR. Ces bibliothèques ne sont pas des espaces de noms XAML mappé à un type valeur par défaut spécifiques à l’infrastructure et par conséquent, requièrent un mappage de préfixe pour l’utilisation XAML.  
  
 Vous pouvez spécifier plusieurs noms de type XAML à l’aide d’une virgule.  
  
 Si les contraintes génériques eux-mêmes utilisent des types génériques, les arguments de type de contrainte imbriqué peuvent être contenus par des parenthèses ().  
  
 Notez que cette définition de `x:TypeArguments` est spécifique aux Services de XAML .NET Framework et à l’aide de stockage CLR. Vous trouverez une définition au niveau du langage dans [ \[MS-XAML\] Section 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="usage-examples"></a>Exemples d’utilisation  
 Pour ces exemples, supposons que les définitions d’espace de noms XAML suivantes sont déclarées :  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>Liste\<chaîne >  
 `<scg:List x:TypeArguments="sys:String" ...>` instancie un nouveau <xref:System.Collections.Generic.List%601> avec un <xref:System.String> argument de type.  
  
### <a name="dictionarystringstring"></a>Dictionnaire\<String, String >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instancie un nouveau <xref:System.Collections.Generic.Dictionary%602> avec deux <xref:System.String> arguments de type.  
  
### <a name="queuekeyvaluepairstringstring"></a>File d’attente < KeyValuePair\<String, String >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instancie un nouveau <xref:System.Collections.Generic.Queue%601> qui a une contrainte de <xref:System.Collections.Generic.KeyValuePair%602> avec les arguments de type de contrainte interne <xref:System.String> et <xref:System.String>.  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>Utilisations XAML générique de XAML 2006 et WPF  
 Pour l’utilisation de XAML 2006 et XAML qui est utilisé pour les applications WPF, les restrictions suivantes existent pour `x:TypeArguments` et utilisations de type générique à partir de XAML en général :  
  
- Seul l’élément racine d’un fichier XAML peut prendre en charge une utilisation XAML générique qui fait référence à un type générique.  
  
- L’élément racine doit mapper à un type générique au moins un argument de type. Par exemple, <xref:System.Windows.Navigation.PageFunction%601>. Les fonctions de page sont le scénario principal pour la prise en charge des génériques de l’utilisation XAML dans WPF.  
  
- L’élément d’objet racine élément XAML pour le modèle générique doit également déclarer une classe partielle à l’aide `x:Class`. Cela est vrai même si l’action de génération de définition d’un WPF.  
  
- `x:TypeArguments` Impossible de référencer les contraintes génériques imbriqués.  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 ou 2006 XAML sans WPF 3.0 ni les WPF 3.5 dépendance  
 Dans les Services XAML .NET Framework pour XAML 2006 ou XAML 2009, les restrictions liées à WPF sur l’utilisation XAML générique sont assouplies. Vous pouvez instancier un élément objet générique à n’importe quelle position dans le balisage XAML prenant en charge la sauvegarde type système et le modèle objet.  
  
 Si vous utilisez XAML 2009 au lieu de mapper le CLR des types pour obtenir les types XAML pour les primitives de langage courantes de base, vous pouvez utiliser [des Types intégrés pour les Primitives de langage XAML courantes](built-in-types-for-common-xaml-language-primitives.md) en tant qu’éléments d’informations dans un `typeString`. Par exemple, vous pouvez déclarer les éléments suivants (les mappages de préfixe ne pas affichés, mais x est l’espace de noms XAML de langage XAML pour XAML 2009) :  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 Dans WPF et lorsque vous ciblez .NET Framework 4, vous pouvez utiliser les fonctionnalités XAML 2009 avec `x:TypeArguments` mais uniquement pour XAML libre (XAML non compilé par balisage). Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009. Si vous avez besoin de compiler le XAML par balisage, vous devez fonctionner selon les restrictions notées dans la section « XAML 2006 et WPF XAML utilisations générique ».  
  
## <a name="see-also"></a>Voir aussi

- [x:Class, directive](x-class-directive.md)
- [x:Type, extension de balisage](x-type-markup-extension.md)
- [Types intégrés pour les primitives associées au langage XAML courant](built-in-types-for-common-xaml-language-primitives.md)
- [Génériques en XAML](generics-in-xaml.md)
