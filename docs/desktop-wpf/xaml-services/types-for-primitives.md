---
title: Types intégrés pour les primitives associées au langage XAML courant
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: 3bd486ee66c5f9a32621416638bb7575025f7dee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071835"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>Types intégrés pour les primitifs communs de langue XAML

XAML 2009 introduit la prise en charge de niveau de langage XAML pour plusieurs types de données qui sont des primitives fréquemment utilisées dans le Common Language Runtime (CLR) et dans d'autres langages de programmation. XAML 2009 ajoute la prise en charge des primitives suivantes : `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`et `x:Array`

## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>Techniques précédentes pour les primitives du langage dans le balisage XAML

 En XAML, pour les versions précédentes de WPF, vous pouviez faire référence aux primitives du langage CLR en mappant l'assembly et l'espace de noms qui contenaient une classe de définition de primitive CLR pour le .NET Framework. La plupart d'entre elles se trouvent dans l'assembly mscorlib et dans l'espace de noms <xref:System> . Par exemple, pour utiliser <xref:System.Int32>, vous pouviez déclarer le mappage suivant (avec un exemple d'utilisation indiqué ensuite) :

```xaml
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Application.Resources>
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>
  </Application.Resources>
</Application>
```

## <a name="xaml-2009-language-primitives"></a>Primitives de langage XAML 2009

Par convention, les primitives de langage pour XAML et tous les autres éléments de langage XAML sont affichés, notamment le préfixe `x:` . C'est ainsi que les éléments de langage XAML sont généralement utilisés dans le balisage réel. Cette convention est suivie de la documentation conceptuelle pour XAML dans WPF, ainsi que dans la spécification XAML.

### <a name="xobject"></a>x:Object

Pour le stockage CLR, la primitive `x:Object` correspond à <xref:System.Object>.

Cette primitive n'est généralement pas utilisée dans le balisage d'application, mais elle peut être utile pour certains scénarios tels que la vérification de l'assignabilité dans un système de type XAML.

### <a name="xboolean"></a>x:Boolean

Pour le stockage CLR, la primitive `x:Boolean` correspond à <xref:System.Boolean>.

XAML analyse les valeurs de `x:Boolean` sans respect de la casse. Notez que `x:Bool` n'est pas une alternative acceptée. Pour la définition de spécification linguistique XAML, voir [ \[les sections MS-XAML\] 5.2.17 et 5.4.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xchar"></a>x:Char

Pour le stockage CLR, la primitive `x:Char` correspond à <xref:System.Char>.

Les types de chaîne et de caractère ont une interaction avec l'encodage global du fichier au niveau XML. Pour la définition de spécification linguistique XAML, voir [ \[les sections\] MS-XAML 5.2.7 et 5.4.1](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xstring"></a>x:String

Pour le stockage CLR, la primitive `x:String` correspond à <xref:System.String>.

Les types de chaîne et de caractère ont une interaction avec l'encodage global du fichier au niveau XML. Pour la définition de spécification linguistique XAML, voir [ \[MS-XAML\] Sections 5.2.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xdecimal"></a>x:Decimal

Pour le stockage CLR, la primitive `x:Decimal` correspond à <xref:System.Decimal>.

L’analyse XAML se fait `en-US` intrinsèquement sous culture. Dans la culture `en-US` , le séparateur approprié pour les composants d'une valeur décimale est toujours le point (`.`), indépendamment des paramètres de culture de l'environnement de développement, ou de la cible cliente éventuelle où le code XAML est chargé au moment de l'exécution.

Pour la définition de spécification linguistique XAML, voir [ \[les sections\] MS-XAML 5.2.14 et 5.4.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xsingle"></a>x:Single

Pour le stockage CLR, la primitive `x:Single` correspond à <xref:System.Single>.

Outre les valeurs numériques, la syntaxe de texte de `x:Single` autorise également les jetons `Infinity`, `-Infinity`et `NaN`. Ces jetons sont traités avec respect de la casse.

`x:Single` peut prendre en charge les valeurs sous forme de notation scientifique, si le premier caractère dans la syntaxe de texte est `e` ou `E`.

Pour la définition de spécification linguistique XAML, voir [ \[les sections\] MS-XAML 5.2.8 et 5.4.2](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xdouble"></a>x:Double

Pour le stockage CLR, la primitive `x:Double` correspond à <xref:System.Double>.

Outre les valeurs numériques, la syntaxe de texte de `x:Double` autorise les jetons `Infinity`, `-Infinity`et `NaN`. Ces jetons sont traités avec respect de la casse.

`x:Double` peut prendre en charge les valeurs sous forme de notation scientifique. Utilisez le caractère `e` ou `E` pour introduire la partie exposant.

Pour la définition de spécification linguistique XAML, voir [ \[les sections\] MS-XAML 5.2.9 et 5.4.3](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint16"></a>x:Int16

Pour le stockage CLR, la primitive `x:Int16` correspond à <xref:System.Int16> et `x:Int16` est considérée comme signée. En XAML, l'absence d'un signe plus (`+`) dans la syntaxe de texte indique implicitement une valeur signée positive.

Pour la définition de spécification linguistique XAML, voir [ \[les sections\] MS-XAML 5.2.11 et 5.4.5](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint32"></a>x:Int32

Pour le stockage CLR, la primitive `x:Int32` correspond à <xref:System.Int32>. `x:Int32` est considérée comme signée. En XAML, l'absence d'un signe plus (`+`) dans la syntaxe de texte indique implicitement une valeur signée positive.

Pour la définition de spécification linguistique XAML, voir [ \[les sections\] MS-XAML 5.2.12 et 5.4.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xint64"></a>x:Int64

Pour le stockage CLR, la primitive `x:Int64` correspond à <xref:System.Int64>. `x:Int64` est considérée comme signée. En XAML, l'absence d'un signe plus (`+`) dans la syntaxe de texte indique implicitement une valeur signée positive.

Pour la définition de spécification linguistique XAML, voir [ \[les sections\] MS-XAML 5.2.13 et 5.4.7](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xtimespan"></a>x:TimeSpan

Pour le stockage CLR, la primitive `x:TimeSpan` correspond à <xref:System.TimeSpan>.

L’analyse XAML pour le format de `en-US` date d’heure se fait intrinsèquement sous la culture.

Pour la définition de spécification linguistique XAML, voir [ \[les sections MS-XAML\] 5.2.16 et 5.4.10](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xuri"></a>x:Uri

Pour le stockage CLR, la primitive `x:Uri` correspond à <xref:System.Uri>.

La vérification des protocoles ne fait pas partie de la définition XAML de `x:Uri`.

Pour la définition de spécification linguistique XAML, voir [ \[les sections\] MS-XAML 5.2.15 et 5.4.9](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xbyte"></a>x:Byte

Pour le stockage CLR, la primitive `x:Byte` correspond à <xref:System.Byte>. <xref:System.Byte>  /  A `x:Byte` est traité comme non signé.

Pour la définition de spécification linguistique XAML, voir [ \[les sections\] MS-XAML 5.2.10 et 5.4.4](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

### <a name="xarray"></a>x:Array

Pour le stockage CLR, la primitive `x:Array` correspond à <xref:System.Array>.

Vous pouvez définir un tableau dans XAML 2006 à l'aide d'une syntaxe d'extension de balisage ; toutefois, la syntaxe XAML 2009 est une primitive définie par le langage qui ne requiert pas l'accès à une extension de balisage. Pour plus d’informations sur la prise en charge de XAML 2006, consultez [x:Array Markup Extension](xarray-markup-extension.md).

Pour la définition de spécification linguistique XAML, voir [ \[MS-XAML\] Sections 5.2.18](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="wpf-support"></a>Prise en charge de WPF

Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour le code XAML qui n'est pas compilé par balisage. Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.

La création de code XAML libre, suivie du chargement de ce code XAML dans une exécution de WPF et dans un graphique d'objets avec <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>constitue un scénario dans lequel vous pouvez utiliser les fonctionnalités XAML 2009 avec WPF. La classe <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> WPF et sa méthode <xref:System.Windows.Markup.XamlReader.Load%2A> peuvent traiter les mots clés de langage et fonctionnalités XAML 2009 dans une représentation de graphique d'objets valide.
