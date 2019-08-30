---
title: TypeConverters et XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 8c39fe75eea5042657cab533a0a557d966802a1b
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169023"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters et XAML
Cette rubrique présente l’objectif de la conversion de types de chaîne comme une fonctionnalité générale du langage XAML. Dans le .NET Framework, la <xref:System.ComponentModel.TypeConverter> classe sert à un objectif particulier dans le cadre de l’implémentation d’une classe personnalisée managée qui peut être utilisée comme valeur de propriété dans l’utilisation d’attribut XAML. Si vous écrivez une classe personnalisée et souhaitez que des instances de votre classe soient utilisables comme valeurs d’attribut définissables XAML, vous devrez peut- <xref:System.ComponentModel.TypeConverterAttribute> être appliquer un à votre classe, <xref:System.ComponentModel.TypeConverter> écrire une classe personnalisée, ou les deux.  

## <a name="type-conversion-concepts"></a>Concepts de conversion de type  
  
### <a name="xaml-and-string-values"></a>XAML et valeurs de chaîne  
 Quand vous définissez une valeur d’attribut dans un fichier XAML, le type initial de cette valeur est une chaîne en texte pur. Même les autres primitives telles <xref:System.Double> que sont initialement des chaînes de texte pour un processeur XAML.  
  
 Un processeur XAML a besoin de deux types d’informations pour pouvoir traiter une valeur d’attribut. Le premier élément d'information est le type valeur de la propriété à définir. N'importe quelle chaîne qui définit une valeur d'attribut et qui est traitée en XAML doit au final être convertie ou résolue en une valeur de ce type. Si la valeur est une primitive comprise par l'analyseur XAML (telle qu'une valeur numérique), une conversion directe de la chaîne est tentée. Si la valeur est une énumération, la chaîne est utilisée pour rechercher une correspondance de nom à une constante nommée dans cette énumération. Si la valeur n’est ni une primitive comprise par l’analyseur, ni une énumération, le type en question doit pouvoir fournir une instance du type ou une valeur, en fonction d’une chaîne convertie. Pour cela, vous devez indiquer une classe de convertisseur de type. Le convertisseur de type est une classe d’assistance qui sert à fournir des valeurs d’une autre classe, pour le scénario XAML et éventuellement pour les appels de code dans le code .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Utilisation du comportement de conversion de types existant en XAML  
 En fonction de votre connaissance des concepts XAML sous-jacents, il se peut que vous utilisiez déjà un comportement de conversion de types dans des applications XAML de base sans vous en rendre compte. Par exemple, WPF définit littéralement des centaines de propriétés qui prennent une valeur de <xref:System.Windows.Point>type. Un <xref:System.Windows.Point> est une valeur qui décrit une coordonnée dans un espace de coordonnées à deux dimensions, et il a en fait simplement <xref:System.Windows.Point.X%2A> deux <xref:System.Windows.Point.Y%2A>propriétés importantes: et. Lorsque vous spécifiez un point en XAML, vous le spécifiez sous la forme d’une chaîne avec un séparateur (généralement <xref:System.Windows.Point.X%2A> une <xref:System.Windows.Point.Y%2A> virgule) entre les valeurs et que vous fournissez. Par exemple : `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 Même ce type simple de <xref:System.Windows.Point> et son utilisation simple en XAML impliquent un convertisseur de type. Dans ce cas, il s’agit <xref:System.Windows.PointConverter>de la classe.  
  
 Le convertisseur de type <xref:System.Windows.Point> pour défini au niveau de la classe simplifie les utilisations de balisage de toutes <xref:System.Windows.Point>les propriétés qui prennent. Sans un convertisseur de type ici, vous auriez besoin de la balise suivante beaucoup plus détaillée pour l’exemple indiqué précédemment :  

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
  
 Les convertisseurs de type existants peuvent généralement être découverts sur les types WPF et .NET Framework en vérifiant une classe (ou propriété) pour <xref:System.ComponentModel.TypeConverterAttribute>la présence d’un appliqué. Cet attribut nomme la classe qui est le convertisseur de type de prise en charge pour les valeurs de ce type, pour les besoins XAML et éventuellement d’autres usages.  
  
### <a name="type-converters-and-markup-extensions"></a>Convertisseurs de type et extensions de balisage  
 Les extensions de balisage et les convertisseurs de types remplissent des rôles orthogonaux quant au comportement du processeur XAML et aux scénarios auxquels ils s’appliquent. Bien que le contexte soit disponible pour les extensions de balisage, le comportement de la conversion de type des propriétés où une extension de balisage fournit une valeur n’est généralement pas vérifié dans les implémentations d’extension de balisage. En d’autres termes, même si une extension de balisage retourne une chaîne de texte comme sortie `ProvideValue`, le comportement de conversion de type associé à cette chaîne tel qu’il est appliqué à une propriété ou un type de valeur de propriété spécifique n’est pas appelé. En général, la fonction d’une extension de balisage consiste à traiter une chaîne et retourner un objet sans faire appel à un convertisseur de type.  
  
 Dans le cadre de la création d’une référence à un objet existant, il est courant d’utiliser une extension de balisage à la place d’un convertisseur de type. Au mieux, un convertisseur de type sans état générerait uniquement une nouvelle instance, ce qui peut ne pas être souhaitable. Pour plus d’informations sur les extensions de balisage, consultez [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Convertisseurs de type natif  
 Dans une implémentation WPF et .NET Framework de l’analyseur XAML, certains types gèrent nativement la conversion de type ; cependant, ces types ne sont pas traditionnellement considérés comme des primitives. Un exemple d'un tel type est <xref:System.DateTime>. La raison est basée sur le fonctionnement de l’architecture .NET Framework: le type <xref:System.DateTime> est défini dans mscorlib, la bibliothèque la plus basique dans .net. <xref:System.DateTime>n’est pas autorisé à être attribué avec un attribut qui provient d’un autre assembly qui introduit<xref:System.ComponentModel.TypeConverterAttribute> une dépendance (is from System). par conséquent, le mécanisme de découverte du convertisseur de type habituel par attribution ne peut pas être pris en charge. À la place, l’analyseur XAML dispose d’une liste des types qui doivent faire l’objet d’un traitement natif et traite ces types de la même façon que les véritables primitives. (Dans le cas <xref:System.DateTime> présent, cela implique un appel à <xref:System.DateTime.Parse%2A>.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implémentation d'un convertisseur de type  
  
### <a name="typeconverter"></a>TypeConverter  
 Dans l' <xref:System.Windows.Point> exemple donné précédemment, la classe <xref:System.Windows.PointConverter> a été mentionnée. Pour les implémentations .NET de XAML, tous les convertisseurs de type utilisés pour le XAML sont des classes qui dérivent <xref:System.ComponentModel.TypeConverter>de la classe de base. La <xref:System.ComponentModel.TypeConverter> classe existait dans les versions de .NET Framework qui précèdent l’existence de XAML; l’une de ses utilisations d’origine consistait à fournir une conversion de chaînes pour les boîtes de dialogue de propriétés dans les concepteurs visuels. Pour XAML, le rôle de <xref:System.ComponentModel.TypeConverter> est développé pour inclure la classe de base pour les conversions de chaînes à chaîne et à partir de chaînes qui permettent d’analyser une valeur d’attribut de chaîne et, éventuellement, de traiter une valeur d’exécution d’une propriété d’objet particulière dans une chaîne pour sérialisation en tant qu’attribut.  
  
 <xref:System.ComponentModel.TypeConverter>définit quatre membres qui sont pertinents pour la conversion vers et à partir de chaînes à des fins de traitement XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Parmi celles-ci, la méthode la <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>plus importante est. Cette méthode convertit la chaîne d’entrée en type d’objet exigé. À proprement parler <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> , la méthode peut être implémentée pour convertir une plus grande plage de types dans le type de destination prévu du convertisseur et, par conséquent, servir des objectifs qui s’étendent au-delà du XAML, tels que la prise en charge des conversions au moment de l’exécution, mais à des fins XAML Il s’agit uniquement du chemin de code qui peut <xref:System.String> traiter une entrée qui est importante.  
  
 La méthode la plus importante suivante <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>est. Si une application est convertie en représentation de balisage (par exemple, si elle est enregistrée en XAML sous forme <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> de fichier), est responsable de la génération d’une représentation de balisage. Dans ce cas, le chemin de code qui est important pour XAML est lorsque vous `destinationType` transmettez un de <xref:System.String> .  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> et <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> sont des méthodes de support utilisées lorsqu'un service interroge les fonctions de l'implémentation <xref:System.ComponentModel.TypeConverter> . Vous devez implémenter ces méthodes pour retourner `true` dans des cas spécifiques au type pris en charge par les méthodes de conversion correspondantes de votre convertisseur. Pour le langage XAML, cela correspond généralement au type <xref:System.String> .  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informations de culture et convertisseurs de type pour XAML  
 Chaque <xref:System.ComponentModel.TypeConverter> implémentation peut avoir sa propre interprétation de ce qui constitue une chaîne valide pour une conversion, et peut également utiliser ou ignorer la description de type passée en tant que paramètres. Vous devez tenir compte d’un élément fondamental en ce qui concerne la culture et la conversion de type XAML. L’utilisation de chaînes localisables comme valeurs d’attribut est intégralement prise en charge par XAML. Mais l’utilisation de cette chaîne localisable comme entrée de convertisseur de type avec des spécifications de culture spécifiques n’est pas prise en charge, car les convertisseurs de types pour les valeurs d’attribut XAML impliquent un comportement d’analyse de langage fixe, à l’aide de la culture `en-US`. Pour plus d’informations sur les raisons de conception de cette restriction, consultez la spécification de langage XAML ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)).  
  
 Par exemple, certaines cultures utilisent une virgule comme séparateur décimal pour les nombres, ce qui peut être un problème. Cela crée un conflit avec de nombreux convertisseurs de types XAML WPF qui utilisent une virgule comme séparateur (pour des raisons historiques : forme X,Y courante ou listes délimitées par des virgules). Même le passage d’une culture dans le XAML voisin (affectation à `Language` ou `xml:lang` de la culture `sl-SI`, un exemple de culture utilisant une virgule comme séparateur décimal) ne résout pas le problème.  
  
### <a name="implementing-convertfrom"></a>Implémentation de ConvertFrom  
 Pour être utilisable en tant qu'implémentation <xref:System.ComponentModel.TypeConverter> qui prend en charge le code XAML, la méthode <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> du convertisseur doit accepter une chaîne comme paramètre `value` . Si la chaîne a un format valide et qu’elle peut être convertie par l' <xref:System.ComponentModel.TypeConverter> implémentation de, l’objet retourné doit prendre en charge un cast vers le type attendu par la propriété. Sinon, l'implémentation <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> doit retourner `null`.  
  
 Chaque <xref:System.ComponentModel.TypeConverter> implémentation peut avoir sa propre interprétation de ce qui constitue une chaîne valide pour une conversion, et peut également utiliser ou ignorer la description de type ou les contextes de culture passés comme paramètres. Cependant, le traitement XAML WPF peut ne pas passer de valeurs au contexte de description de type dans tous les cas, et également ne pas passer la culture en fonction de `xml:lang`.  
  
> [!NOTE]
> N’utilisez pas les accolades, en particulier {, comme élément possible de format de chaîne. Ces caractères sont réservés comme entrée et sortie d’une séquence d’extension de balisage.  
  
### <a name="implementing-convertto"></a>Implémentation de ConvertTo  
 La méthode<xref:System.ComponentModel.TypeConverter.ConvertTo%2A> peut être utilisée pour assurer la prise en charge de la sérialisation. La prise en charge de la sérialisation via <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> pour votre type personnalisé et son convertisseur de type n'est pas une spécification absolue. Toutefois, si vous implémentez un contrôle ou que vous utilisez la sérialisation dans le cadre des fonctionnalités ou de la conception de la classe, vous devez implémenter <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Pour être utilisable en tant <xref:System.ComponentModel.TypeConverter> qu’implémentation qui prend en charge <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> XAML, la méthode de ce convertisseur doit accepter une instance du type (ou une valeur `value` ) prise en charge en tant que paramètre. Lorsque le `destinationType` paramètre est le type <xref:System.String>, l’objet retourné doit pouvoir être casté en <xref:System.String>. La chaîne retournée doit représenter une valeur sérialisée de `value`. Idéalement, le format de sérialisation que vous choisissez doit pouvoir générer la même valeur si cette chaîne était passée à l' <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implémentation du même convertisseur, sans perte significative d’informations.  
  
 Si la valeur ne peut pas être sérialisée ou que le convertisseur ne prend pas en charge <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> la sérialisation, `null`l’implémentation doit retourner et est autorisé à lever une exception dans ce cas. Toutefois, si vous levez des exceptions, vous devez signaler l’impossibilité d’utiliser cette conversion dans le <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> cadre de votre implémentation de afin que la meilleure <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> pratique qui consiste à vérifier en premier pour éviter les exceptions soit prise en charge.  
  
 Si `destinationType` le paramètre n’est pas <xref:System.String>de type, vous pouvez choisir votre propre gestion de convertisseur. En général, vous revenez au traitement de l’implémentation de base, qui <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> , dans avec, lève une exception spécifique.  
  
### <a name="implementing-canconvertto"></a>Implémentation de CanConvertTo  
 Votre implémentation de <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> doit retourner la valeur `true` pour `destinationType` de type <xref:System.String>, et sinon déférer à l'implémentation de base.  
  
### <a name="implementing-canconvertfrom"></a>Implémentation de CanConvertFrom  
 Votre implémentation de <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> doit retourner la valeur `true` pour `sourceType` de type <xref:System.String>, et sinon déférer à l'implémentation de base.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Application de TypeConverterAttribute  
 Pour que votre convertisseur de type personnalisé soit utilisé comme convertisseur de type agissant pour une classe personnalisée par un processeur XAML, vous devez appliquer <xref:System.ComponentModel.TypeConverterAttribute> à votre définition de classe. La propriété <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> que vous spécifiez via l'attribut doit être le nom de type du convertisseur de type personnalisé. Une fois cet attribut appliqué, quand un processeur XAML gère des valeurs où le type de propriété utilise votre type de classe personnalisée, il peut entrer des chaînes et retourner des instances d’objet.  
  
 Vous pouvez également fournir un convertisseur de type en fonction de la propriété. Au lieu d’appliquer <xref:System.ComponentModel.TypeConverterAttribute> un à la définition de classe, appliquez-le à une définition de propriété (la définition `get` principale, et non les / `set` implémentations qu’il contient). Le type de la propriété doit correspondre au type traité par votre convertisseur de type personnalisé. Avec cet attribut appliqué, lorsqu'un processeur XAML gère des valeurs de cette propriété, il peut traiter des chaînes d'entrée et retourner des instances d'objet. La technique de conversion de type par propriété est particulièrement utile si vous choisissez d’utiliser un type de propriété à partir de Microsoft .NET Framework ou d’une autre bibliothèque où vous ne pouvez pas contrôler la <xref:System.ComponentModel.TypeConverterAttribute> définition de classe et ne pouvez pas l’appliquer.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.TypeConverter>
- [Vue d’ensemble du langage XAML (WPF)](xaml-overview-wpf.md)
- [Extensions de balisage et XAML WPF](markup-extensions-and-wpf-xaml.md)
- [Syntaxe XAML en détail](xaml-syntax-in-detail.md)
