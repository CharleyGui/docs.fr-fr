---
title: TypeConverters et XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 94cfce44d5702e0550310723ec56184096165436
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187299"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters et XAML
Cette rubrique présente l’objectif de la conversion de types de chaîne comme une fonctionnalité générale du langage XAML. Dans le cadre .NET, la <xref:System.ComponentModel.TypeConverter> classe sert un but particulier dans le cadre de la mise en œuvre d’une classe personnalisée gérée qui peut être utilisée comme valeur de propriété dans l’utilisation d’attributS XAML. Si vous écrivez une classe personnalisée, et que vous voulez que les instances de votre classe <xref:System.ComponentModel.TypeConverterAttribute> soient utilisables en tant que valeurs d’attributs définies XAML, vous devrez peut-être appliquer un à votre classe, écrire une classe personnalisée, <xref:System.ComponentModel.TypeConverter> ou les deux.  

## <a name="type-conversion-concepts"></a>Concepts de conversion de type  
  
### <a name="xaml-and-string-values"></a>XAML et valeurs de chaîne  
 Quand vous définissez une valeur d’attribut dans un fichier XAML, le type initial de cette valeur est une chaîne en texte pur. Même d’autres <xref:System.Double> primitifs tels que sont d’abord des chaînes de texte à un processeur XAML.  
  
 Un processeur XAML a besoin de deux types d’informations pour pouvoir traiter une valeur d’attribut. Le premier élément d'information est le type valeur de la propriété à définir. N'importe quelle chaîne qui définit une valeur d'attribut et qui est traitée en XAML doit au final être convertie ou résolue en une valeur de ce type. Si la valeur est une primitive comprise par l'analyseur XAML (telle qu'une valeur numérique), une conversion directe de la chaîne est tentée. Si la valeur est une énumération, la chaîne est utilisée pour rechercher une correspondance de nom à une constante nommée dans cette énumération. Si la valeur n’est ni une primitive comprise par l’analyseur, ni une énumération, le type en question doit pouvoir fournir une instance du type ou une valeur, en fonction d’une chaîne convertie. Pour cela, vous devez indiquer une classe de convertisseur de type. Le convertisseur de type est une classe d’assistance qui sert à fournir des valeurs d’une autre classe, pour le scénario XAML et éventuellement pour les appels de code dans le code .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Utilisation du comportement de conversion de types existant en XAML  
 En fonction de votre connaissance des concepts XAML sous-jacents, il se peut que vous utilisiez déjà un comportement de conversion de types dans des applications XAML de base sans vous en rendre compte. Par exemple, WPF définit littéralement des centaines <xref:System.Windows.Point>de propriétés qui prennent une valeur de type . A <xref:System.Windows.Point> est une valeur qui décrit une coordonnées dans un espace de coordonnées <xref:System.Windows.Point.X%2A> bidimensionnelles, et il a vraiment juste deux propriétés importantes: et <xref:System.Windows.Point.Y%2A>. Lorsque vous spécifiez un point dans XAML, vous le spécifiez comme une chaîne avec un délimitant (généralement une virgule) entre les <xref:System.Windows.Point.X%2A> valeurs que <xref:System.Windows.Point.Y%2A> vous fournissez. Par exemple : `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 Même ce type <xref:System.Windows.Point> simple et son utilisation simple dans XAML impliquent un convertisseur de type. Dans ce cas, <xref:System.Windows.PointConverter>c’est la classe .  
  
 Le convertisseur <xref:System.Windows.Point> de type pour défini au niveau de la classe <xref:System.Windows.Point>rationalise les utilisations de balisage de toutes les propriétés qui prennent . Sans un convertisseur de type ici, vous auriez besoin de la balise suivante beaucoup plus détaillée pour l’exemple indiqué précédemment :  

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.StartPoint>
    <Point X="0" Y="0"/>
  </LinearGradientBrush.StartPoint>
  <LinearGradientBrush.EndPoint>
    <Point X="1" Y="1"/>
  </LinearGradientBrush.EndPoint>
</LinearGradientBrush>
 ```
  
 L’utilisation d’une chaîne de conversion de type ou d’une syntaxe équivalente plus détaillée est une question de style de codage. Votre workflow d’outils XAML peut également influencer la définition des valeurs. Certains outils XAML ont tendance à émettre la forme la plus détaillée du balisage, car il est plus facile de parcourir les vues du concepteur ou son propre mécanisme de sérialisation.  
  
 Les convertisseurs de type existants peuvent généralement être découverts sur les types WPF <xref:System.ComponentModel.TypeConverterAttribute>et .NET Framework en vérifiant une classe (ou une propriété) pour la présence d’une application . Cet attribut nomme la classe qui est le convertisseur de type de prise en charge pour les valeurs de ce type, pour les besoins XAML et éventuellement d’autres usages.  
  
### <a name="type-converters-and-markup-extensions"></a>Convertisseurs de type et extensions de balisage  
 Les extensions de balisage et les convertisseurs de types remplissent des rôles orthogonaux quant au comportement du processeur XAML et aux scénarios auxquels ils s’appliquent. Bien que le contexte soit disponible pour les extensions de balisage, le comportement de la conversion de type des propriétés où une extension de balisage fournit une valeur n’est généralement pas vérifié dans les implémentations d’extension de balisage. En d’autres termes, même si une extension de balisage retourne une chaîne de texte comme sortie `ProvideValue`, le comportement de conversion de type associé à cette chaîne tel qu’il est appliqué à une propriété ou un type de valeur de propriété spécifique n’est pas appelé. En général, la fonction d’une extension de balisage consiste à traiter une chaîne et retourner un objet sans faire appel à un convertisseur de type.  
  
 Dans le cadre de la création d’une référence à un objet existant, il est courant d’utiliser une extension de balisage à la place d’un convertisseur de type. Au mieux, un convertisseur de type sans état générerait uniquement une nouvelle instance, ce qui peut ne pas être souhaitable. Pour plus d’informations sur les extensions de balisage, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Convertisseurs de type natif  
 Dans une implémentation WPF et .NET Framework de l’analyseur XAML, certains types gèrent nativement la conversion de type ; cependant, ces types ne sont pas traditionnellement considérés comme des primitives. Un exemple d'un tel type est <xref:System.DateTime>. La raison en est basée sur le fonctionnement de <xref:System.DateTime> l’architecture cadre .NET: le type est défini dans mscorlib, la bibliothèque la plus basique en .NET. <xref:System.DateTime>n’est pas autorisé à être attribué avec un attribut qui<xref:System.ComponentModel.TypeConverterAttribute> vient d’une autre assemblée qui introduit une dépendance (est du système) de sorte que le mécanisme habituel de découverte de convertisseur de type en attribuant ne peut pas être pris en charge. À la place, l’analyseur XAML dispose d’une liste des types qui doivent faire l’objet d’un traitement natif et traite ces types de la même façon que les véritables primitives. (Dans le <xref:System.DateTime> cas de cela <xref:System.DateTime.Parse%2A>implique un appel à .)  
  
<a name="Implementing_a_Type_Converter"></a>
## <a name="implementing-a-type-converter"></a>Implémentation d'un convertisseur de type  
  
### <a name="typeconverter"></a>TypeConverter  
 Dans <xref:System.Windows.Point> l’exemple donné <xref:System.Windows.PointConverter> précédemment, la classe a été mentionnée. Pour les implémentations .NET de XAML, tous les convertisseurs de <xref:System.ComponentModel.TypeConverter>type qui sont utilisés à des fins XAML sont des classes qui dérivent de la classe de base . La <xref:System.ComponentModel.TypeConverter> classe existait dans les versions de .NET Framework qui précèdent l’existence de XAML; l’un de ses usages originaux était de fournir la conversion de chaîne pour les dialogues de propriété dans les concepteurs visuels. Pour XAML, le <xref:System.ComponentModel.TypeConverter> rôle de est élargi pour inclure être la classe de base pour les conversions à cordes et à chaîne qui permettent d’analyser une valeur d’attribut de chaîne, et peut-être le traitement d’une valeur de temps d’exécution d’une propriété d’objet particulier de nouveau dans une chaîne pour la sérialisation comme un attribut.  
  
 <xref:System.ComponentModel.TypeConverter>définit quatre membres qui sont pertinents pour la conversion à et depuis les chaînes à des fins de traitement XAML :  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Parmi ceux-ci, la <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>méthode la plus importante est . Cette méthode convertit la chaîne d’entrée en type d’objet exigé. Strictement parlant, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> la méthode pourrait être mise en œuvre pour convertir un éventail beaucoup plus large de types dans le type de destination prévu par le convertisseur, et ainsi <xref:System.String> servir des fins qui s’étendent au-delà de XAML tels que les conversions de temps d’exécution de soutien, mais pour les fins XAML c’est seulement la voie de code qui peut traiter une entrée qui importe.  
  
 La méthode la <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>plus importante est . Si une application est convertie en représentation de majoration (par exemple, si <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> elle est enregistrée à XAML en tant que fichier), est responsable de la production d’une représentation de majoration. Dans ce cas, le chemin de code qui importe `destinationType` pour <xref:System.String> XAML est quand vous passez un de .  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> et <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> sont des méthodes de support utilisées lorsqu'un service interroge les fonctions de l'implémentation <xref:System.ComponentModel.TypeConverter> . Vous devez implémenter ces méthodes pour retourner `true` dans des cas spécifiques au type pris en charge par les méthodes de conversion correspondantes de votre convertisseur. Pour le langage XAML, cela correspond généralement au type <xref:System.String> .  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informations de culture et convertisseurs de type pour XAML  

 Chaque <xref:System.ComponentModel.TypeConverter> implémentation peut avoir sa propre interprétation de ce qui constitue une chaîne valide pour une conversion, et peut également utiliser ou ignorer la description de type adoptée comme paramètres. Vous devez tenir compte d’un élément fondamental en ce qui concerne la culture et la conversion de type XAML. L’utilisation de chaînes localisables comme valeurs d’attribut est intégralement prise en charge par XAML. Mais l’utilisation de cette chaîne localisable comme entrée de convertisseur de type avec des spécifications de culture spécifiques n’est pas prise en charge, car les convertisseurs de types pour les valeurs d’attribut XAML impliquent un comportement d’analyse de langage fixe, à l’aide de la culture `en-US`. Pour plus d’informations sur les raisons de conception de cette restriction, vous devriez consulter la spécification linguistique XAML ([\[MS-XAML\]](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf).  
  
 Par exemple, certaines cultures utilisent une virgule comme séparateur décimal pour les nombres, ce qui peut être un problème. Cela crée un conflit avec de nombreux convertisseurs de types XAML WPF qui utilisent une virgule comme séparateur (pour des raisons historiques : forme X,Y courante ou listes délimitées par des virgules). Même le passage d’une culture dans le XAML voisin (affectation à `Language` ou `xml:lang` de la culture `sl-SI`, un exemple de culture utilisant une virgule comme séparateur décimal) ne résout pas le problème.  
  
### <a name="implementing-convertfrom"></a>Implémentation de ConvertFrom  
 Pour être utilisable en tant qu'implémentation <xref:System.ComponentModel.TypeConverter> qui prend en charge le code XAML, la méthode <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> du convertisseur doit accepter une chaîne comme paramètre `value` . Si la chaîne était en format valide, <xref:System.ComponentModel.TypeConverter> et peut être convertie par la mise en œuvre, alors l’objet retourné doit prendre en charge un plâtre au type attendu par la propriété. Sinon, l'implémentation <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> doit retourner `null`.  
  
 Chaque <xref:System.ComponentModel.TypeConverter> implémentation peut avoir sa propre interprétation de ce qui constitue une chaîne valide pour une conversion, et peut également utiliser ou ignorer la description de type ou les contextes de culture adoptés comme paramètres. Cependant, le traitement XAML WPF peut ne pas passer de valeurs au contexte de description de type dans tous les cas, et également ne pas passer la culture en fonction de `xml:lang`.  
  
> [!NOTE]
> N’utilisez pas les accolades, en particulier {, comme élément possible de format de chaîne. Ces caractères sont réservés comme entrée et sortie d’une séquence d’extension de balisage.  
  
### <a name="implementing-convertto"></a>Implémentation de ConvertTo  
 La méthode<xref:System.ComponentModel.TypeConverter.ConvertTo%2A> peut être utilisée pour assurer la prise en charge de la sérialisation. La prise en charge de la sérialisation via <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> pour votre type personnalisé et son convertisseur de type n'est pas une spécification absolue. Toutefois, si vous implémentez un contrôle ou que vous utilisez la sérialisation dans le cadre des fonctionnalités ou de la conception de la classe, vous devez implémenter <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Pour être utilisable comme implémentation <xref:System.ComponentModel.TypeConverter> qui prend en charge XAML, la <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> méthode pour `value` ce convertisseur doit accepter une instance du type (ou une valeur) étant pris en charge comme le paramètre. Lorsque `destinationType` le paramètre <xref:System.String>est le type, puis l’objet retourné doit être en mesure d’être jeté comme <xref:System.String>. La chaîne retournée doit représenter une valeur sérialisée de `value`. Idéalement, le format de sérialisation que vous choisissez devrait être <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> capable de générer la même valeur si cette chaîne était transmise à la mise en œuvre du même convertisseur, sans perte significative d’informations.  
  
 Si la valeur ne peut pas être sérialisée <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> ou si `null`le convertisseur ne prend pas en charge la sérialisation, la mise en œuvre doit revenir et est autorisée à faire une exception dans ce cas. Mais si vous faites des exceptions, vous devez signaler l’incapacité d’utiliser cette conversion dans le cadre de votre <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> mise en œuvre afin que la meilleure pratique de vérification avec <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> d’abord pour éviter les exceptions est pris en charge.  
  
 Si `destinationType` le paramètre <xref:System.String>n’est pas de type, vous pouvez choisir votre propre manipulation de convertisseur. En règle générale, vous reveniez à <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> la gestion de la mise en œuvre de base, qui dans le plus bas soulève une exception spécifique.  
  
### <a name="implementing-canconvertto"></a>Implémentation de CanConvertTo  
 Votre implémentation de <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> doit retourner la valeur `true` pour `destinationType` de type <xref:System.String>, et sinon déférer à l'implémentation de base.  
  
### <a name="implementing-canconvertfrom"></a>Implémentation de CanConvertFrom  
 Votre implémentation de <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> doit retourner la valeur `true` pour `sourceType` de type <xref:System.String>, et sinon déférer à l'implémentation de base.  
  
<a name="Applying_the_TypeConverterAttribute"></a>
## <a name="applying-the-typeconverterattribute"></a>Application de TypeConverterAttribute  
 Pour que votre convertisseur de type personnalisé soit utilisé comme convertisseur de type agissant pour <xref:System.ComponentModel.TypeConverterAttribute> une classe personnalisée par un processeur XAML, vous devez appliquer la définition de votre classe. La propriété <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> que vous spécifiez via l'attribut doit être le nom de type du convertisseur de type personnalisé. Une fois cet attribut appliqué, quand un processeur XAML gère des valeurs où le type de propriété utilise votre type de classe personnalisée, il peut entrer des chaînes et retourner des instances d’objet.  
  
 Vous pouvez également fournir un convertisseur de type en fonction de la propriété. Au lieu <xref:System.ComponentModel.TypeConverterAttribute> d’appliquer une définition de classe, appliquez-la `get` / `set` à une définition de propriété (la définition principale, et non les implémentations en son sein). Le type de la propriété doit correspondre au type traité par votre convertisseur de type personnalisé. Avec cet attribut appliqué, lorsqu'un processeur XAML gère des valeurs de cette propriété, il peut traiter des chaînes d'entrée et retourner des instances d'objet. La technique de conversion de type propriété est particulièrement utile si vous choisissez d’utiliser un type de propriété de <xref:System.ComponentModel.TypeConverterAttribute> Microsoft .NET Framework ou d’une autre bibliothèque où vous ne pouvez pas contrôler la définition de classe et ne peut pas appliquer un là-bas.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.TypeConverter>
- [Vue d’ensemble du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [Syntaxe XAML en détail](xaml-syntax-in-detail.md)
