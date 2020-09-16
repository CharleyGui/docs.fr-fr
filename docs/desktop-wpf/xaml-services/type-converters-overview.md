---
title: Vue d'ensemble des convertisseurs de types pour XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: 6e78210178fda65bb3baad0d24eb3a20cd6f2a3e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540111"
---
# <a name="overview-of-type-converters-for-xaml"></a>Vue d’ensemble des convertisseurs de type pour XAML

Les convertisseurs de type fournissent la logique nécessaire à un writer d'objet qui convertit une chaîne de balisage XAML en objets particuliers d'un graphique d'objets. Dans les services XAML .NET, le convertisseur de type doit être une classe qui dérive de <xref:System.ComponentModel.TypeConverter> . Certains convertisseurs prennent également en charge le chemin d'enregistrement XAML et peuvent être utilisés pour sérialiser un objet sous forme de chaîne dans le balisage de sérialisation. Cette rubrique décrit comment et quand les convertisseurs de type en XAML sont appelés, et fournit des conseils d'implémentation pour les substitutions de méthode de <xref:System.ComponentModel.TypeConverter>.

## <a name="type-conversion-concepts"></a>Concepts de conversion de type

Les sections suivantes expliquent les concepts de base relatifs à la façon dont XAML utilise les chaînes et comment les Writers d’objet des services XAML .NET utilisent des convertisseurs de type pour traiter certaines valeurs de chaîne rencontrées dans une source XAML.

### <a name="xaml-and-string-values"></a>XAML et valeurs de chaîne

Lorsque vous définissez une valeur d'attribut dans un fichier XAML, le type initial de cette valeur est une chaîne dans un sens général et une valeur d'attribut de chaîne dans le sens de XML. Même les autres primitives telles que <xref:System.Double> sont initialement des chaînes pour un processeur XAML.

Dans la plupart des cas, un processeur XAML a besoin de deux éléments d'informations pour traiter une valeur d'attribut. Le premier élément d'information est le type valeur de la propriété à définir. N'importe quelle chaîne qui définit une valeur d'attribut et qui est traitée en XAML doit au final être convertie ou résolue en une valeur de ce type. Si la valeur est une primitive comprise par l'analyseur XAML (telle qu'une valeur numérique), une conversion directe de la chaîne est tentée. Si la valeur de l'attribut référence une énumération, la chaîne fournie est utilisée pour rechercher une correspondance de nom avec une constante nommée dans cette énumération. Si la valeur n’est pas une primitive comprise par l’analyseur ou un nom de constante d’une énumération, le type applicable doit pouvoir fournir une valeur ou une référence basée sur une chaîne convertie.

> [!NOTE]
> Les directives de langage XAML n'utilisent pas de convertisseur de type.

### <a name="type-converters-and-markup-extensions"></a>Convertisseurs de type et extensions de balisage

Les utilisations d'extension de balisage doivent être gérées par un processeur XAML avant qu'il ne recherche le type de propriété et d'autres considérations. Par exemple, si une propriété définie en tant qu'attribut a généralement une conversion de type, mais que dans un cas particulier, elle est définie par une utilisation d'extension de balisage, le comportement d'extension de balisage est traité en premier. Faire référence à un objet existant constitue une situation courante où il est nécessaire d'utiliser une extension de balisage. Pour ce scénario, un convertisseur de type sans état peut uniquement générer une nouvelle instance, ce qui n'est peut-être pas souhaitable. Pour plus d’informations sur les extensions de balisage, consultez [Markup Extensions for XAML Overview](markup-extensions-overview.md).

### <a name="native-type-converters"></a>Convertisseurs de type natif

Dans les implémentations de services XAML Windows Presentation Foundation (WPF) et .NET, il existe certains types CLR qui gèrent la conversion de type natif. Toutefois, ces types CLR ne sont pas considérés conventionnellement comme des primitives. Un exemple d'un tel type est <xref:System.DateTime>. L'une des raisons réside dans le fonctionnement de l'architecture .NET Framework : le type <xref:System.DateTime> est défini dans mscorlib, la bibliothèque la plus élémentaire du .NET. <xref:System.DateTime> n’est pas autorisé à être attribué avec un attribut qui provient d’un autre assembly qui introduit une dépendance ( <xref:System.ComponentModel.TypeConverterAttribute> est du système). Par conséquent, le mécanisme de découverte du convertisseur de type habituel par attribution ne peut pas être pris en charge. À la place, l'analyseur XAML dispose d'une liste des types qui doivent faire l'objet d'un traitement natif et traite ces types de la même façon que les véritables primitives. Dans le cas de <xref:System.DateTime>, ce traitement implique un appel à <xref:System.DateTime.Parse%2A>.

## <a name="implementing-a-type-converter"></a>Implémentation d'un convertisseur de type

Les sections suivantes traitent de l'API de la classe <xref:System.ComponentModel.TypeConverter> .

### <a name="typeconverter"></a>TypeConverter

Sous les services XAML .NET, tous les convertisseurs de type utilisés pour le XAML sont des classes qui dérivent de la classe de base <xref:System.ComponentModel.TypeConverter> . La classe <xref:System.ComponentModel.TypeConverter> existait dans les versions du .NET Framework antérieures à l'introduction de XAML ; l'un des scénarios <xref:System.ComponentModel.TypeConverter> d'origine consistait à fournir une conversion de chaînes pour les éditeurs de propriétés dans les concepteurs visuels.

Pour XAML, le rôle de <xref:System.ComponentModel.TypeConverter> a été étendu. Aux fins du langage XAML, <xref:System.ComponentModel.TypeConverter> est la classe de base permettant la prise en charge de certaines conversions en chaînes et à partir de chaînes. Les conversions à partir de chaînes permettent d'analyser une valeur d'attribut de chaîne à partir du code XAML. Les conversions en chaînes permettent de reconvertir une valeur d'exécution d'une propriété d'objet particulière en attribut en XAML pour la sérialisation.

<xref:System.ComponentModel.TypeConverter> définit quatre membres qui sont utiles pour la conversion en chaînes et à partir de chaînes à des fins de traitement XAML :

- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>

- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>

- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>

- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>

Parmi ces membres, la méthode la plus importante est <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>, qui convertit la chaîne d'entrée en type d'objet requis. La méthode <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> peut être implémentée pour convertir une plage plus large de types vers le type de destination prévu du convertisseur. Par conséquent, elle peut remplir des fonctions qui dépassent le cadre du langage XAML, telles que la prise en charge des conversions au moment de l'exécution. Toutefois, pour l'utilisation de XAML, seul le chemin de code capable de traiter une entrée <xref:System.String> est important.

La deuxième méthode la plus importante est <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> . Si une application est convertie en représentation de balisage (par exemple, si elle est enregistrée en XAML sous forme de fichier), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> est impliqué dans le scénario plus vaste d’un TEXTWRITER XAML pour produire une représentation de balisage. Dans ce cas, le chemin de code important pour XAML est lorsque l'appelant passe un `destinationType` de <xref:System.String>.

<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> et <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> sont des méthodes de support utilisées lorsqu'un service interroge les fonctions de l'implémentation <xref:System.ComponentModel.TypeConverter> . Vous devez implémenter ces méthodes pour retourner `true` dans des cas spécifiques au type pris en charge par les méthodes de conversion correspondantes de votre convertisseur. Pour le langage XAML, cela correspond généralement au type <xref:System.String> .

### <a name="culture-information-and-type-converters-for-xaml"></a>Informations de culture et convertisseurs de type pour XAML

Chaque implémentation <xref:System.ComponentModel.TypeConverter> peut interpréter de façon unique ce qui constitue une chaîne valide dans le cadre d'une conversion ; elle peut également utiliser ou ignorer la description de type passée en tant que paramètres. Considération importante relative à la culture et à la conversion de type XAML : bien que l'utilisation de chaînes localisables en tant que valeurs d'attribut soit prise en charge par XAML, vous ne pouvez pas employer ces chaînes localisables comme entrée de convertisseur de type avec des spécifications de culture particulières. Cette restriction est due au fait que les convertisseurs de types des valeurs d'attribut XAML impliquent un comportement de traitement XAML de langage fixe qui utilise la culture `en-US` . Pour plus d’informations sur les raisons de conception de cette restriction, consultez la spécification de langage XAML ([ \[ MS-XAML \] ](/previous-versions/msp-n-p/ff650760(v=pandp.10))) ou [vue d’ensemble de la globalisation et de la localisation WPF](/dotnet/desktop/wpf/advanced/wpf-globalization-and-localization-overview).

Par exemple, certaines cultures utilisent une virgule au lieu d'un point comme séparateur décimal pour les nombres sous forme de chaîne, ce qui peut poser un problème. Cette utilisation crée un conflit avec le comportement de nombreux convertisseurs de type existants, qui consiste à utiliser une virgule comme délimiteur. Le passage d'une culture via `xml:lang` dans le code XAML environnant ne résout pas le problème.

### <a name="implementing-convertfrom"></a>Implémentation de ConvertFrom

Pour être utilisable en tant qu'implémentation <xref:System.ComponentModel.TypeConverter> qui prend en charge le code XAML, la méthode <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> du convertisseur doit accepter une chaîne comme paramètre `value` . Si la chaîne a un format valide et qu'elle peut être convertie par l'implémentation de <xref:System.ComponentModel.TypeConverter> , l'objet retourné doit prendre en charge un cast vers le type attendu par la propriété. Sinon, l'implémentation <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> doit retourner `null`.

Chaque implémentation de <xref:System.ComponentModel.TypeConverter> peut interpréter de façon unique ce qui constitue une chaîne valide dans le cadre d'une conversion ; elle peut également utiliser ou ignorer la description de type ou les contextes de culture passés en tant que paramètres. Cependant, le traitement XAML WPF ne passe pas nécessairement des valeurs au contexte de description de type dans tous les cas, ni de culture en fonction de `xml:lang`.

> [!NOTE]
> N’utilisez pas les accolades ( {} ), en particulier l’accolade ouvrante ({), en tant qu’élément de votre format de chaîne. Ces caractères sont réservés comme entrée et sortie d’une séquence d’extension de balisage.

Il convient de lever une exception si votre convertisseur de type doit avoir accès à un service XAML à partir du writer d’objet des services XAML .NET, mais que l' <xref:System.IServiceProvider.GetService%2A> appel effectué par rapport au contexte ne retourne pas ce service.

### <a name="implementing-convertto"></a>Implémentation de ConvertTo

La méthode<xref:System.ComponentModel.TypeConverter.ConvertTo%2A> peut être utilisée pour assurer la prise en charge de la sérialisation. La prise en charge de la sérialisation via <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> pour votre type personnalisé et son convertisseur de type n'est pas une spécification absolue. Toutefois, si vous implémentez un contrôle ou que vous utilisez la sérialisation dans le cadre des fonctionnalités ou de la conception de la classe, vous devez implémenter <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.

Pour être utilisable en tant qu'implémentation de <xref:System.ComponentModel.TypeConverter> qui prend en charge XAML, la méthode <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> de ce convertisseur doit accepter une instance du type (ou une valeur) prise en charge comme paramètre `value` . Lorsque le paramètre `destinationType` est de type <xref:System.String>, l'objet retourné doit pouvoir être casté en <xref:System.String>. La chaîne retournée doit représenter une valeur sérialisée de `value`. Idéalement, le format de sérialisation que vous choisissez doit pouvoir générer la même valeur que si cette chaîne était passée à l'implémentation de <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> du même convertisseur, sans perte significative d'informations.

Si la valeur ne peut pas être sérialisée ou que le convertisseur ne prend pas en charge la sérialisation, l'implémentation de <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> doit retourner la valeur `null` et peut lever une exception. Toutefois, si vous levez des exceptions, vous devez signaler que cette conversion ne peut pas être utilisée dans le cadre de votre implémentation de <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> afin que la meilleure pratique qui consiste à effectuer d'abord une vérification avec <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> pour éviter les exceptions soit prise en charge.

Si le paramètre `destinationType` n'est pas de type <xref:System.String>, vous pouvez choisir votre propre gestion de convertisseur. En général, vous rétablissez le traitement de l'implémentation de base, ce qui, dans la méthode <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> de base, lève une exception spécifique.

Il convient de lever une exception si votre convertisseur de type doit avoir accès à un service XAML à partir du writer d’objet des services XAML .NET, mais que l' <xref:System.IServiceProvider.GetService%2A> appel effectué par rapport au contexte ne retourne pas ce service.

### <a name="implementing-canconvertfrom"></a>Implémentation de CanConvertFrom

Votre implémentation de <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> doit retourner la valeur `true` pour `sourceType` de type <xref:System.String> , et sinon déférer à l'implémentation de base. Ne levez pas d'exceptions à partir de la méthode <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.

### <a name="implementing-canconvertto"></a>Implémentation de CanConvertTo

Votre implémentation de <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> doit retourner la valeur `true` pour `destinationType` de type <xref:System.String>, et sinon déférer à l'implémentation de base. Ne levez pas d'exceptions à partir de la méthode <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.

## <a name="applying-the-typeconverterattribute"></a>Application de TypeConverterAttribute

Pour que votre convertisseur de type personnalisé soit utilisé comme convertisseur de type agissant pour une classe personnalisée par les services XAML .NET, vous devez appliquer <xref:System.ComponentModel.TypeConverterAttribute> à votre définition de classe. La propriété <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> que vous spécifiez via l'attribut doit être le nom de type du convertisseur de type personnalisé. Si vous appliquez cet attribut, lorsqu'un processeur XAML gère des valeurs où le type de propriété utilise votre type de classe personnalisée, il peut entrer des chaînes et retourner des instances d'objet.

Vous pouvez également fournir un convertisseur de type en fonction de la propriété. Au lieu d’appliquer un <xref:System.ComponentModel.TypeConverterAttribute> à la définition de classe, appliquez-le à une définition de propriété (la définition principale, et non les `get` / `set` implémentations qu’il contient). Le type de la propriété doit correspondre au type traité par votre convertisseur de type personnalisé. Avec cet attribut appliqué, lorsqu'un processeur XAML gère des valeurs de cette propriété, il peut traiter des chaînes d'entrée et retourner des instances d'objet. La technique de conversion de type par propriété est utile si vous choisissez d’utiliser un type de propriété à partir de Microsoft .NET Framework ou d’une autre bibliothèque où vous ne pouvez pas contrôler la définition de classe et ne pouvez pas l’appliquer <xref:System.ComponentModel.TypeConverterAttribute> .

Pour fournir un comportement de conversion de type pour un membre attaché personnalisé, appliquez <xref:System.ComponentModel.TypeConverterAttribute> à la méthode `Get` d'accesseur du modèle d'implémentation du membre attaché.

## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Accès au contexte de fournisseur de services à partir d'une implémentation de l'extension du balisage

Les services disponibles sont les mêmes pour tous les convertisseurs de valeurs. La seule différence réside dans le mode de réception du contexte de service par chaque convertisseur de valeurs. L’accès aux services et les services disponibles sont documentés dans la rubrique [Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions.md).

## <a name="type-converters-in-the-xaml-node-stream"></a>Convertisseurs de type et flux de nœud XAML

Si vous utilisez un flux de nœud XAML, l'action d'un convertisseur de type n'est pas encore exécutée ou n'a pas encore produit de résultat final. Dans un chemin de chargement, la chaîne d'attribut dont le type doit finalement être converti pour qu'elle puisse être chargée demeure sous la forme d'une valeur de texte dans un membre de début et un membre de fin. Le convertisseur de type qui est finalement requis pour cette opération peut être déterminé à l'aide de la propriété <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> . Toutefois, l'obtention d'une valeur valide à partir de <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> repose sur la disponibilité d'un contexte de schéma XAML permettant d'accéder à ces informations via le membre sous-jacent ou le type de la valeur d'objet que le membre utilise. L'appel réel du comportement de conversion de type requiert également le contexte de schéma XAML car cette opération nécessite un mappage de type et la création d'une instance de convertisseur.

## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.TypeConverterAttribute>
- [Convertisseurs de types et extensions de balisage pour XAML](type-converters-and-markup-extensions.md)
- [Vue d’ensemble du langage XAML (WPF)](../fundamentals/xaml.md)
