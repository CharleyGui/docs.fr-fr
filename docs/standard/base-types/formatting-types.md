---
title: Mise en forme des types dans .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data formatting [.NET Framework]
- dates [.NET Framework], formatting
- date formatting [.NET Framework]
- number formatting [.NET Framework]
- ToString method
- custom cultural settings [.NET Framework]
- numbers [.NET Framework], formatting
- formatting strings [.NET Framework]
- time [.NET Framework], formatting
- currency [.NET Framework], formatting
- types [.NET Framework], formatting
- format specifiers [.NET Framework]
- times [.NET Framework], formatting
- culture [.NET Framework], formatting
- formatting [.NET Framework], types supported
- base types [.NET Framework], formatting
- custom formatting [.NET Framework]
- strings [.NET Framework], formatting
ms.assetid: 0d1364da-5b30-4d42-8e6b-03378343343f
ms.openlocfilehash: a1f4d9107427140bcfa6b49bc8a850432fb204f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75348250"
---
# <a name="format-types-in-net"></a>Types de format en .NET

La mise en forme est le processus de conversion d'une instance d'une classe, d'une structure ou d'une valeur d'énumération en représentation sous forme de chaîne, généralement pour exposer la chaîne obtenue aux utilisateurs ou pour qu'elle soit désérialisée afin de restaurer le type de données d'origine. Cette conversion peut présenter plusieurs difficultés :

- La manière dont les valeurs sont stockées en interne ne reflète pas nécessairement celle dont les utilisateurs souhaitent les voir. Par exemple, un numéro de téléphone peut être stocké sous la forme 8009999999, ce qui n'est pas convivial. Il devrait plutôt être affiché sous la forme 800-999-9999. Consultez la section [Chaînes de format personnalisé](#custom-format-strings) pour obtenir un exemple d'une telle mise en forme d'un nombre.

- La conversion d'un objet en sa représentation sous forme de chaîne n'est pas toujours intuitive. Par exemple, il n'est pas évident de savoir comment doit s'afficher la représentation sous forme de chaîne d'un objet Temperature ou Person. Pour obtenir un exemple illustrant la mise en forme d'un objet Temperature selon différentes manières, consultez la section [Chaînes de format standard](#standard-format-strings) .

- Les valeurs requièrent souvent une mise en forme qui tient compte de la culture. Par exemple, dans une application qui utilise des nombre pour refléter des valeurs monétaires, les chaînes numériques doivent inclure le symbole monétaire, le séparateur de groupes (qui, dans la plupart des cultures, est le séparateur des milliers) et le symbole décimal qui correspondent à la culture actuelle. Par exemple, consultez la section [Formatting sensible à la culture avec les fournisseurs de formats.](#culture-sensitive-formatting-with-format-providers)

- Une application peut avoir à afficher la même valeur de différentes manières. Par exemple, une application peut représenter un membre d'énumération en affichant une représentation sous forme de chaîne de son nom ou en affichant sa valeur sous-jacente. Pour obtenir un exemple illustrant la mise en forme d'un membre de l'énumération <xref:System.DayOfWeek> selon différentes manières, consultez la section [Chaînes de format standard](#standard-format-strings) .

> [!NOTE]
> La mise en forme convertit la valeur d'un type en une représentation sous forme de chaîne. L'analyse est l'opération inverse de la mise en forme. Une opération d'analyse crée une instance d'un type de données à partir de sa représentation sous forme de chaîne. Pour plus d’informations sur la conversion de chaînes en d’autres types de données, consultez [Parsing Strings](../../../docs/standard/base-types/parsing-strings.md).

.NET assure une prise en charge évoluée de la mise en forme qui permet aux développeurs de surmonter ces difficultés.

## <a name="formatting-in-net"></a>Mise en forme dans .NET

Le mécanisme de base de la mise en forme est l'implémentation par défaut de la méthode <xref:System.Object.ToString%2A?displayProperty=nameWithType>, décrite dans la section [Mise en forme par défaut à l'aide de la méthode ToString](#default-formatting-using-the-tostring-method), plus loin dans cette rubrique. Toutefois, .NET propose différentes manières de modifier et d’étendre sa prise en charge par défaut de la mise en forme. Ces options en question sont les suivantes :

- Substitution de la méthode <xref:System.Object.ToString%2A?displayProperty=nameWithType> pour définir une représentation sous forme de chaîne personnalisée de la valeur d'un objet. Pour plus d’informations, consultez la section [Override the ToString Method](#override-the-tostring-method) plus tard dans ce sujet.

- Définition de spécificateurs de format qui permettent à la représentation sous forme de chaîne de la valeur d'un objet de prendre plusieurs formes. Par exemple, dans l'instruction suivante, le spécificateur de format "X" convertit un entier en la représentation sous forme de chaîne d'une valeur hexadécimale.

     [!code-csharp[Conceptual.Formatting.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#3)]
     [!code-vb[Conceptual.Formatting.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#3)]

     Pour plus d'informations sur les spécificateurs de format, consultez la section [Méthode ToString et chaînes de format](#the-tostring-method-and-format-strings) .

- Utilisation de fournisseurs de format pour tirer parti des conventions de mise en forme d'une culture spécifique. Par exemple, l'instruction suivante affiche une valeur monétaire en utilisant les conventions de mise en forme de la culture en-US.

     [!code-csharp[Conceptual.Formatting.Overview#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/specifier1.cs#10)]
     [!code-vb[Conceptual.Formatting.Overview#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/specifier1.vb#10)]

     Pour plus d’informations sur le formatage avec les fournisseurs de formats, consultez la section [Fournisseurs de formats.](#culture-sensitive-formatting-with-format-providers)

- Implémentation de l'interface <xref:System.IFormattable> pour prendre en charge la conversion de chaînes avec la classe <xref:System.Convert> et la mise en forme composite. Pour plus d'informations, consultez la section [Interface IFormattable](#the-iformattable-interface) .

- Utilisation de la mise en forme composite pour incorporer la représentation sous forme de chaîne d'une valeur dans une chaîne plus grande. Pour plus d'informations, consultez la section [Mise en forme composite](#composite-formatting) .

- Implémentation d' <xref:System.ICustomFormatter> et d' <xref:System.IFormatProvider> pour fournir une solution de mise en forme personnalisée et complète. Pour plus d'informations, consultez la section [Mise en forme personnalisée avec ICustomFormatter](#custom-formatting-with-icustomformatter) .

Les sections suivantes étudient ces méthodes de conversion d'un objet en sa représentation sous forme de chaîne.

## <a name="default-formatting-using-the-tostring-method"></a>Mise en forme par défaut à l’aide de la méthode ToString

Chaque type qui est dérivé d' <xref:System.Object?displayProperty=nameWithType> hérite automatiquement d'une méthode `ToString` sans paramètre, laquelle retourne le nom du type par défaut. L'exemple suivant illustre la méthode `ToString` par défaut. Il définit une classe nommée `Automobile` qui n'a pas d'implémentation. Lorsque cette classe est instanciée et que sa méthode `ToString` est appelée, elle affiche son nom de type. Notez que la méthode `ToString` n'est pas appelée explicitement dans cet exemple. La méthode <xref:System.Console.WriteLine%28System.Object%29?displayProperty=nameWithType> appelle implicitement la méthode `ToString` de l'objet qui lui est passé comme argument.

[!code-csharp[Conceptual.Formatting.Overview#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/default1.cs#1)]
[!code-vb[Conceptual.Formatting.Overview#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/default1.vb#1)]

> [!WARNING]
> En commençant par Windows 8.1, <xref:Windows.Foundation.IStringable> le Windows Runtime inclut une interface avec une seule méthode, [IStringable.ToString](xref:Windows.Foundation.IStringable.ToString%2A), qui fournit un support de formatage par défaut. Toutefois, nous recommandons que les types managés n'implémentent pas l'interface `IStringable` . Pour plus d’informations, consultez la section « Windows Runtime et interface `IStringable` » dans la page de référence de <xref:System.Object.ToString%2A?displayProperty=nameWithType>.

Étant donné que tous les types autres que les interfaces sont dérivés de <xref:System.Object>, ces fonctionnalités sont fournies automatiquement à vos classes ou structures personnalisées. Toutefois, les fonctionnalités offertes par la méthode `ToString` par défaut sont limitées : Bien qu'elle identifie le type, elle ne fournit aucune information relative à une instance du type. Pour fournir une représentation sous forme de chaîne d'un objet qui donne des informations sur cet objet, vous devez substituer la méthode `ToString` .

> [!NOTE]
> Les structures héritent de <xref:System.ValueType>, qui, à son tour, est dérivé d' <xref:System.Object>. Bien que <xref:System.ValueType> substitue <xref:System.Object.ToString%2A?displayProperty=nameWithType>, son implémentation est identique.

## <a name="override-the-tostring-method"></a>Remplacer la méthode ToString

L'utilité de l'affichage du nom d'un type est souvent limitée et ne permet pas aux consommateurs de vos types de différencier une instance d'une autre. Toutefois, vous pouvez substituer la méthode `ToString` pour fournir une représentation plus utile de la valeur d'un objet. L'exemple suivant définit un objet `Temperature` et substitue sa méthode `ToString` pour afficher la température en degrés Celsius.

[!code-csharp[Conceptual.Formatting.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/overrides1.cs#2)]
[!code-vb[Conceptual.Formatting.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/overrides1.vb#2)]

Dans .NET, la méthode `ToString` de chaque type valeur primitif a été écrasée de façon à afficher la valeur de l’objet plutôt que son nom. Le tableau suivant montre la substitution pour chaque type primitif. Notez que la plupart des méthodes substituées appellent une autre surcharge de la méthode `ToString` et lui passent le spécificateur de format "G", qui définit le format général pour son type, ainsi qu'un objet <xref:System.IFormatProvider> qui représente la culture actuelle.

|Type|Substitution de ToString|
|----------|-----------------------|
|<xref:System.Boolean>|Retourne <xref:System.Boolean.TrueString?displayProperty=nameWithType> ou <xref:System.Boolean.FalseString?displayProperty=nameWithType>.|
|<xref:System.Byte>|Appelle `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur <xref:System.Byte> pour la culture actuelle.|
|<xref:System.Char>|Retourne le caractère sous forme de chaîne.|
|<xref:System.DateTime>|Appelle `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` afin de mettre en forme la valeur de date et d'heure pour la culture actuelle.|
|<xref:System.Decimal>|Appelle `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur <xref:System.Decimal> pour la culture actuelle.|
|<xref:System.Double>|Appelle `Double.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur <xref:System.Double> pour la culture actuelle.|
|<xref:System.Int16>|Appelle `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur <xref:System.Int16> pour la culture actuelle.|
|<xref:System.Int32>|Appelle `Int32.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur <xref:System.Int32> pour la culture actuelle.|
|<xref:System.Int64>|Appelle `Int64.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur <xref:System.Int64> pour la culture actuelle.|
|<xref:System.SByte>|Appelle `SByte.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur <xref:System.SByte> pour la culture actuelle.|
|<xref:System.Single>|Appelle `Single.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur <xref:System.Single> pour la culture actuelle.|
|<xref:System.UInt16>|Appelle `UInt16.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur <xref:System.UInt16> pour la culture actuelle.|
|<xref:System.UInt32>|Appelle `UInt32.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur <xref:System.UInt32> pour la culture actuelle.|
|<xref:System.UInt64>|Appelle `UInt64.ToString("G", NumberFormatInfo.CurrentInfo)` afin de mettre en forme la valeur <xref:System.UInt64> pour la culture actuelle.|

## <a name="the-tostring-method-and-format-strings"></a>Méthode ToString et chaînes de format

Le recours à la méthode `ToString` ou la substitution de `ToString` ne valent que lorsqu'un objet a une seule représentation sous forme de chaîne possible. Toutefois, la valeur d'un objet a souvent plusieurs représentations. Par exemple, une température peut être exprimée en degrés Fahrenheit, Celsius ou Kelvin. De même, la valeur entière 10 peut être représentée de plusieurs façons, dont 10, 10,0, 1,0e01 ou $10,00.

Pour permettre à une même valeur d’avoir plusieurs représentations sous forme de chaîne, .NET utilise des chaînes de format. Une chaîne de format est une chaîne qui contient un ou plusieurs spécificateurs de format prédéfinis, constitués d'un ou de plusieurs caractères servant à définir la manière dont la méthode `ToString` doit mettre en forme sa sortie. La chaîne de format est ensuite passée en tant que paramètre à la méthode `ToString` de l'objet et détermine la manière dont la représentation sous forme de chaîne de la valeur de cet objet doit apparaître.

Dans .NET, tous les types numériques, types de date et d’heure et types énumération prennent en charge un jeu prédéfini de spécificateurs de format. Vous pouvez aussi utiliser des chaînes de format pour définir plusieurs représentations sous forme de chaîne de vos types de données définis par l'application.

### <a name="standard-format-strings"></a>Chaînes de format standard

Une chaîne de format standard comprend un spécificateur de format unique, qui est un caractère alphabétique définissant la représentation sous forme de chaîne de l'objet auquel il s'applique, ainsi qu'un spécificateur de précision facultatif qui affecte le nombre de chiffres affichés dans la chaîne de résultat. Si le spécificateur de précision est omis ou n'est pas pris en charge, un spécificateur de format standard équivaut à une chaîne de format standard.

.NET définit un jeu de spécificateurs de format standard pour tous les types numériques, types de date et d’heure et types énumération. Par exemple, chacune de ces catégories prend en charge un spécificateur de format standard "G", lequel définit une représentation sous forme de chaîne générale d'une valeur de ce type.

Les chaînes de format standard pour les types énumération contrôlent directement la représentation sous forme de chaîne d'une valeur. Les chaînes de format passées à la méthode `ToString` d'une valeur d'énumération déterminent si la valeur est affichée en utilisant son nom de chaîne (spécificateurs de format "G" et "F"), sa valeur intégrale sous-jacente (spécificateur de format "D") ou sa valeur hexadécimale (spécificateur de format "X"). L'exemple suivant illustre l'utilisation de chaînes de format standard pour mettre en forme une valeur d'énumération <xref:System.DayOfWeek> .

[!code-csharp[Conceptual.Formatting.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/standard1.cs#4)]
[!code-vb[Conceptual.Formatting.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/standard1.vb#4)]

Pour plus d’informations sur les chaînes de format d’énumération, consultez [Enumeration Format Strings](../../../docs/standard/base-types/enumeration-format-strings.md).

Les chaînes de format standard pour les types numériques définissent généralement une chaîne de résultat dont l'apparence précise est contrôlée par une ou plusieurs valeurs de propriété. Par exemple, le spécificateur de format "C" met en forme un nombre en tant que valeur monétaire. Lorsque vous appelez la méthode `ToString` avec, comme seul paramètre, le spécificateur de format "C", les valeurs des propriétés suivantes de l'objet <xref:System.Globalization.NumberFormatInfo> de la culture actuelle sont utilisées pour définir la représentation sous forme de chaîne de la valeur numérique :

- Propriété <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A> , qui spécifie le symbole monétaire de la culture actuelle.

- Propriété <xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A> ou <xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A> , qui retourne un entier déterminant :

  - la position du symbole monétaire ;

  - si les valeurs négatives sont indiquées par un signe négatif devant, par un signe négatif derrière ou par des parenthèses ;

  - si un espace apparaît entre la valeur numérique et le symbole monétaire.

- Propriété <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A> , qui définit le nombre de chiffres fractionnaires dans la chaîne de résultat.

- Propriété <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A> , qui définit le symbole de séparateur décimal dans la chaîne de résultat.

- Propriété <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A> , qui définit le symbole du séparateur de groupes.

- Propriété <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A> , qui définit le nombre de chiffres de chaque groupe situé à gauche du séparateur décimal.

- Propriété <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> , qui détermine le signe négatif utilisé dans la chaîne de résultat si les parenthèses ne sont pas utilisées pour indiquer des valeurs négatives.

De plus, les chaînes de format numériques peuvent inclure un spécificateur de précision. La signification de ce spécificateur dépend de la chaîne de format avec laquelle il est utilisé, mais il indique généralement le nombre total de chiffres ou le nombre de chiffres fractionnaires qui doivent s'afficher dans la chaîne de résultat. Par exemple, le code suivant utilise la chaîne numérique standard "X4" et un spécificateur de précision pour créer une valeur de chaîne qui comprend quatre chiffres hexadécimaux.

[!code-csharp[Conceptual.Formatting.Overview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/precisionspecifier1.cs#6)]
[!code-vb[Conceptual.Formatting.Overview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/precisionspecifier1.vb#6)]

Pour plus d’informations sur les chaînes de format numériques standard, consultez [Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md).

Les chaînes de format standard pour les valeurs de date et d'heure sont des alias de chaînes de format personnalisées stockées par une propriété <xref:System.Globalization.DateTimeFormatInfo> particulière. Par exemple, appeler la méthode `ToString` d'une valeur de date et d'heure avec le spécificateur de format "D" affiche la date et l'heure en utilisant la chaîne de format personnalisée stockée dans la propriété <xref:System.Globalization.DateTimeFormatInfo.LongDatePattern%2A?displayProperty=nameWithType> de la culture actuelle. (Pour plus d’informations sur les chaînes de format personnalisés, voir la [section suivante](#custom-format-strings).) L’exemple suivant illustre cette relation.

[!code-csharp[Conceptual.Formatting.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/alias1.cs#5)]
[!code-vb[Conceptual.Formatting.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/alias1.vb#5)]

Pour plus d’informations sur les chaînes de format de date et heure standard, consultez [Standard Date and Time Format Strings](../../../docs/standard/base-types/standard-date-and-time-format-strings.md).

Vous pouvez aussi utiliser des chaînes de format standard pour définir la représentation sous forme de chaîne produite par la méthode `ToString(String)` d'un objet défini par l'application. Vous pouvez définir les spécificateurs de format standard spécifiques que votre objet prend en charge, et déterminer s'ils respectent la casse. Votre implémentation de la méthode `ToString(String)` doit prendre en charge les éléments suivants :

- Spécificateur de format "G" qui représente un format habituel ou commun de l'objet. La surcharge sans paramètre de la méthode `ToString` de votre objet doit appeler sa surcharge `ToString(String)` et lui passer la chaîne de format standard "G".

- Prise en charge d'un spécificateur de format qui est égal à une référence null (`Nothing` en Visual Basic). Un spécificateur de format qui est égal à une référence null doit être considéré comme équivalent au spécificateur de format "G".

Par exemple, une classe `Temperature` peut stocker en interne la température en degrés Celsius et utiliser des spécificateurs de format pour représenter la valeur de l'objet `Temperature` en degrés Celsius, Fahrenheit et Kelvin. L'exemple suivant en est l'illustration.

[!code-csharp[Conceptual.Formatting.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/appstandard1.cs#7)]
[!code-vb[Conceptual.Formatting.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/appstandard1.vb#7)]

### <a name="custom-format-strings"></a>Chaînes de format personnalisées

Outre les chaînes de format standard, .NET définit des chaînes de format personnalisées pour les valeurs numériques et les valeurs de date et d’heure. Une chaîne de format personnalisée se compose d'un ou de plusieurs spécificateurs de format personnalisés qui définissent la représentation sous forme de chaîne d'une valeur. Par exemple, la chaîne de format de date et d'heure personnalisée "yyyy\mm\dd hh:mm:ffff t zzz" convertit une date en sa représentation sous forme de chaîne "2008/11/15 07:45:00.0000 P -08:00" pour la culture en-US. De même, la chaîne de format personnalisée "0000" convertit la valeur entière 12 en "0012". Pour obtenir la liste complète des chaînes de format personnalisées, consultez [Custom Date and Time Format Strings](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) et [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md).

Si une chaîne de format se compose d'un seul spécificateur de format personnalisé, le spécificateur de format doit être précédé du symbole de pourcentage (%) pour éviter toute confusion avec un spécificateur de format standard. L'exemple suivant utilise le spécificateur de format personnalisé "M" pour afficher un nombre à un chiffre ou à deux chiffres du mois d'une date particulière.

[!code-csharp[Conceptual.Formatting.Overview#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/singlecustom1.cs#8)]
[!code-vb[Conceptual.Formatting.Overview#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/singlecustom1.vb#8)]

De nombreuses chaînes de format standard pour les valeurs de date et d'heure sont des alias de chaînes de format personnalisées qui sont définies par les propriétés de l'objet <xref:System.Globalization.DateTimeFormatInfo> . Les chaînes de format personnalisées offrent également une souplesse considérable en matière de mise en forme définie par l'application pour les valeurs numériques ou les valeurs de date et d'heure. Vous pouvez définir vos propres chaînes de résultat personnalisées à la fois pour les valeurs numériques et pour les valeurs de date et d'heure en combinant plusieurs spécificateurs de format personnalisés dans une chaîne de format personnalisée unique. L'exemple suivant définit une chaîne de format personnalisée qui affiche le jour de la semaine entre parenthèses après le nom du mois, le jour et l'année.

[!code-csharp[Conceptual.Formatting.Overview#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/custom1.cs#9)]
[!code-vb[Conceptual.Formatting.Overview#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/custom1.vb#9)]

L’exemple ci-dessous définit une chaîne de format personnalisée qui affiche une valeur <xref:System.Int64> sous la forme d’un numéro de téléphone américain standard à sept chiffres avec son indicatif régional.

[!code-csharp[Conceptual.Formatting.Overview#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/telnumber1.cs#21)]
[!code-vb[Conceptual.Formatting.Overview#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/telnumber1.vb#21)]

Bien que les chaînes de format standard puissent généralement gérer la plupart des besoins de mise en forme pour vos types définis par l'application, vous pouvez également définir des spécificateurs de format personnalisés pour mettre en forme vos types.

### <a name="format-strings-and-net-types"></a>Chaînes de format et types .NET

Tous les types numériques (c’est-à-dire, les types <xref:System.Byte>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64> et <xref:System.Numerics.BigInteger>), ainsi que les types <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan> et <xref:System.Guid>, et tous les types énumération, prennent en charge la mise en forme avec des chaînes de format. Pour plus d’informations sur les chaînes de format spécifiques prises en charge par chaque type, consultez les rubriques suivantes :

|Intitulé|Définition|
|-----------|----------------|
|[Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées de valeurs numériques.|
|[Chaînes de format numérique personnalisées](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les valeurs numériques.|
|[Chaînes de format de date et d'heure standard](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Décrit des chaînes de format standard qui créent des représentations courantes de valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset> sous forme de chaînes.|
|[Chaînes personnalisées de format de date et d’heure](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Décrit des chaînes de format personnalisées qui créent des formats propres à l'application pour les valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset>.|
|[Chaînes de format TimeSpan standard](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées d'intervalles de temps.|
|[Chaînes de format TimeSpan personnalisées](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les intervalles de temps.|
|[Chaînes de format d’énumération](../../../docs/standard/base-types/enumeration-format-strings.md)|Décrit les chaînes de format standard qui sont utilisées pour créer des représentations sous forme de chaîne de valeurs d'énumération.|
|<xref:System.Guid.ToString%28System.String%29?displayProperty=nameWithType>|Décrit les chaînes de format standard pour les valeurs <xref:System.Guid> .|

## <a name="culture-sensitive-formatting-with-format-providers"></a>Formatage sensible à la culture avec les fournisseurs de formats

Si les spécificateurs de format vous permettent de personnaliser la mise en forme d'objets, la production, pour ces derniers, d'une représentation sous forme de chaîne explicite requiert souvent des informations de mise en forme supplémentaires. Par exemple, la mise en forme d'un nombre en tant que valeur monétaire en utilisant la chaîne de format standard "C" ou une chaîne de format personnalisée telle que "$ #, #.00" requiert au minimum l'existence d'informations à inclure dans la chaîne mise en forme concernant le symbole monétaire, le séparateur de groupes et le séparateur décimal appropriés. Dans .NET, ces informations de mise en forme supplémentaires sont disponibles sur l’interface <xref:System.IFormatProvider>, laquelle est fournie comme paramètre d’une ou plusieurs surcharges de la méthode `ToString` de types numériques et de types de date et d’heure. Des implémentations de <xref:System.IFormatProvider> sont utilisées dans .NET pour prendre en charge la mise en forme propre à la culture. L'exemple suivant montre comment la représentation d'un objet sous forme de chaîne évolue lorsqu'il est mis en forme avec trois objets <xref:System.IFormatProvider> représentant des cultures différentes.

[!code-csharp[Conceptual.Formatting.Overview#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformatprovider1.cs#11)]
[!code-vb[Conceptual.Formatting.Overview#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformatprovider1.vb#11)]

L'interface <xref:System.IFormatProvider> inclut une méthode, <xref:System.IFormatProvider.GetFormat%28System.Type%29>, qui a un seul paramètre spécifiant le type d'objet qui fournit les informations de mise en forme. Si la méthode peut fournir un objet de ce type, elle le retourne. Sinon, elle retourne une référence null (`Nothing` en Visual Basic).

<xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> est une méthode de rappel. Lorsque vous appelez une surcharge de méthode `ToString` qui inclut un paramètre <xref:System.IFormatProvider> , elle appelle la méthode <xref:System.IFormatProvider.GetFormat%2A> de cet objet <xref:System.IFormatProvider> . La méthode <xref:System.IFormatProvider.GetFormat%2A> est chargée de retourner les informations de mise en forme requises, spécifiées par son paramètre `formatType` , à la méthode `ToString` .

Certaines méthodes de mise en forme ou de conversion de chaînes incluent un paramètre de type <xref:System.IFormatProvider>, mais la valeur de ce paramètre est souvent ignorée lorsque la méthode est appelée. Le tableau suivant répertorie certaines des méthodes de mise en forme qui utilisent le paramètre et le type de l'objet <xref:System.Type> qu'elles passent à la méthode <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> .

|Méthode|Type de paramètre `formatType`|
|------------|------------------------------------|
|Méthode`ToString` de types numériques|<xref:System.Globalization.NumberFormatInfo?displayProperty=nameWithType>|
|Méthode`ToString` de types de date et d'heure|<xref:System.Globalization.DateTimeFormatInfo?displayProperty=nameWithType>|
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|<xref:System.ICustomFormatter?displayProperty=nameWithType>|

> [!NOTE]
> Les méthodes `ToString` des types numériques et des types de date et d'heure sont surchargées, et seules certaines des surcharges incluent un paramètre <xref:System.IFormatProvider> . Si une méthode n'a pas de paramètre de type <xref:System.IFormatProvider>, l'objet retourné par la propriété <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> est passé à la place. Par exemple, un appel à la méthode <xref:System.Int32.ToString?displayProperty=nameWithType> par défaut a, pour résultat, un appel de méthode semblable au suivant : `Int32.ToString("G", System.Globalization.CultureInfo.CurrentCulture)`.

.NET propose trois classes qui implémentent <xref:System.IFormatProvider> :

- <xref:System.Globalization.DateTimeFormatInfo>, une classe qui fournit des informations de mise en forme pour les valeurs de date et d'heure pour une culture spécifique. Son implémentation de <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> retourne une instance d'elle-même.

- <xref:System.Globalization.NumberFormatInfo>, une classe qui fournit des informations de mise en forme des nombres pour une culture spécifique. Son implémentation de <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> retourne une instance d'elle-même.

- <xref:System.Globalization.CultureInfo>. Son implémentation de <xref:System.IFormatProvider.GetFormat%2A?displayProperty=nameWithType> peut retourner un objet <xref:System.Globalization.NumberFormatInfo> pour fournir des informations de mise en forme des nombres ou un objet <xref:System.Globalization.DateTimeFormatInfo> pour fournir des informations de mise en forme des valeurs de date et d'heure.

Vous pouvez aussi implémenter votre propre fournisseur de format en remplacement de l'une de ces classes. Toutefois, la méthode <xref:System.IFormatProvider.GetFormat%2A> de votre implémentation doit retourner un objet du type répertorié dans le tableau précédent s'il doit fournir des informations de mise en forme à la méthode `ToString` .

### <a name="culture-sensitive-formatting-of-numeric-values"></a>Mise en forme dépendante de la culture des valeurs numériques

Par défaut, la mise en forme des valeurs numériques est dépendante de la culture. Si vous ne spécifiez pas de culture lorsque vous appelez une méthode de mise en forme, les conventions de mise en forme de la culture actuelle du thread sont utilisées. Ceci est illustré dans l'exemple ci-dessous où la culture actuelle du thread est changée quatre fois avant que la méthode <xref:System.Decimal.ToString%28System.String%29?displayProperty=nameWithType> soit appelée. Dans chaque cas, la chaîne obtenue reflète les conventions de mise en forme de la culture actuelle. Ceci tient au fait que les méthodes `ToString` et `ToString(String)` encapsulent les appels à la méthode `ToString(String, IFormatProvider)` de chaque type numérique.

[!code-csharp[Conceptual.Formatting.Overview#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific3.cs#19)]
[!code-vb[Conceptual.Formatting.Overview#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific3.vb#19)]

Vous pouvez également mettre en forme une valeur numérique pour une culture spécifique en appelant une surcharge `ToString` dotée d'un paramètre `provider` et en lui passant l'un ou l'autre des éléments suivants :

- Un objet <xref:System.Globalization.CultureInfo> représentant la culture dont les conventions de mise en forme doivent être utilisées. Sa méthode <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> retourne la valeur de la propriété <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> , qui est l'objet <xref:System.Globalization.NumberFormatInfo> qui fournit des informations de mise en forme propres à la culture pour les valeurs numériques.

- Un objet <xref:System.Globalization.NumberFormatInfo> définissant les conventions de mise en forme propres à la culture qui doivent être utilisées. Sa méthode <xref:System.Globalization.NumberFormatInfo.GetFormat%2A> retourne une instance d'elle-même.

L'exemple suivant utilise des objets <xref:System.Globalization.NumberFormatInfo> qui représentent les cultures Anglais (États-Unis) et Anglais (Royaume-Uni), ainsi que les cultures neutres Français et Russe pour mettre en forme un nombre à virgule flottante.

[!code-csharp[Conceptual.Formatting.Overview#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific4.cs#20)]
[!code-vb[Conceptual.Formatting.Overview#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific4.vb#20)]

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a>Mise en forme dépendante de la culture des valeurs de date et d’heure

Par défaut, la mise en forme des valeurs de date et d'heure est dépendante de la culture. Si vous ne spécifiez pas de culture lorsque vous appelez une méthode de mise en forme, les conventions de mise en forme de la culture actuelle du thread sont utilisées. Ceci est illustré dans l'exemple ci-dessous où la culture actuelle du thread est changée quatre fois avant que la méthode <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> soit appelée. Dans chaque cas, la chaîne obtenue reflète les conventions de mise en forme de la culture actuelle. Ceci tient au fait que les méthodes <xref:System.DateTime.ToString?displayProperty=nameWithType>, <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType>et <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> encapsulent les appels aux méthodes <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> et <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> .

[!code-csharp[Conceptual.Formatting.Overview#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific1.cs#17)]
[!code-vb[Conceptual.Formatting.Overview#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific1.vb#17)]

Vous pouvez également mettre en forme une valeur de date et d'heure pour une culture spécifique en appelant une surcharge <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> dotée d'un paramètre `provider` et en lui passant l'un ou l'autre des éléments suivants :

- Un objet <xref:System.Globalization.CultureInfo> représentant la culture dont les conventions de mise en forme doivent être utilisées. Sa méthode <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> retourne la valeur de la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> , qui est l'objet <xref:System.Globalization.DateTimeFormatInfo> qui fournit des informations de mise en forme propres à la culture pour les valeurs de date et d'heure.

- Un objet <xref:System.Globalization.DateTimeFormatInfo> définissant les conventions de mise en forme propres à la culture qui doivent être utilisées. Sa méthode <xref:System.Globalization.DateTimeFormatInfo.GetFormat%2A> retourne une instance d'elle-même.

L'exemple suivant utilise des objets <xref:System.Globalization.DateTimeFormatInfo> qui représentent les cultures Anglais (États-Unis) et Anglais (Royaume-Uni), ainsi que les cultures neutres Français et Russe pour mettre en forme une date.

[!code-csharp[Conceptual.Formatting.Overview#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/culturespecific2.cs#18)]
[!code-vb[Conceptual.Formatting.Overview#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/culturespecific2.vb#18)]

## <a name="the-iformattable-interface"></a>Interface IFormattable

En règle générale, les types qui surchargent la méthode `ToString` avec une chaîne de format et un paramètre <xref:System.IFormatProvider> implémentent également l'interface <xref:System.IFormattable> . Cette interface comprend un seul membre, <xref:System.IFormattable.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, qui inclut comme paramètres une chaîne de format et un fournisseur de format.

L'implémentation de l'interface <xref:System.IFormattable> pour votre classe définie par l'application présente deux avantages :

- Prise en charge de la conversion de chaînes par la classe <xref:System.Convert> . Les appels aux méthodes <xref:System.Convert.ToString%28System.Object%29?displayProperty=nameWithType> et <xref:System.Convert.ToString%28System.Object%2CSystem.IFormatProvider%29?displayProperty=nameWithType> appellent automatiquement votre implémentation d' <xref:System.IFormattable> .

- Prise en charge de la mise en forme composite. Si un élément de mise en forme qui inclut une chaîne de format est utilisé pour mettre en forme votre type personnalisé, le Common Language Runtime appelle automatiquement votre implémentation d' <xref:System.IFormattable> et lui passe la chaîne de format. Pour plus d’informations sur le <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>formatage composite avec des méthodes telles que ou , voir la section [Formatting composite.](#composite-formatting)

L'exemple suivant définit une classe `Temperature` qui implémente l'interface <xref:System.IFormattable> . Il prend en charge les spécificateurs de format "C" ou "G" pour afficher la température en Celsius, le spécificateur de format "F" pour afficher la température en Fahrenheit et le spécificateur de format "K" pour afficher la température en Kelvin.

[!code-csharp[Conceptual.Formatting.Overview#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#12)]
[!code-vb[Conceptual.Formatting.Overview#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#12)]

L'exemple suivant instancie un objet `Temperature` . Il appelle ensuite la méthode <xref:System.Convert.ToString%2A> et utilise plusieurs chaînes de format composites pour obtenir des représentations sous forme de chaîne différentes d'un objet `Temperature` . Chacun de ces appels de méthode appelle, à son tour, l'implémentation d' <xref:System.IFormattable> de la classe `Temperature` .

[!code-csharp[Conceptual.Formatting.Overview#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/iformattable.cs#13)]
[!code-vb[Conceptual.Formatting.Overview#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/iformattable.vb#13)]

## <a name="composite-formatting"></a>Mise en forme composite

Certaines méthodes, telles que <xref:System.String.Format%2A?displayProperty=nameWithType> et <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>, prennent en charge la mise en forme composite. Une chaîne de format composite est un genre de modèle retournant une seule chaîne qui incorpore la représentation sous forme de chaîne de zéro, un ou plusieurs objets. Chaque objet est représenté dans la chaîne de format composite par un élément de mise en forme indexé. L'index de l'élément de mise en forme correspond à la position de l'objet qu'il représente dans la liste de paramètres de la méthode. Les index sont de base zéro. Par exemple, dans l'appel suivant à la méthode <xref:System.String.Format%2A?displayProperty=nameWithType>, le premier élément de mise en forme, `{0:D}`, est remplacé par la représentation sous forme de chaîne de `thatDate` ; le deuxième élément de mise en forme, `{1}`, est remplacé par la représentation sous forme de chaîne `item1` ; le troisième élément de mise en forme, `{2:C2}`, est remplacé par la représentation sous forme de chaîne de `item1.Value`.

[!code-csharp[Conceptual.Formatting.Overview#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite1.cs#14)]
[!code-vb[Conceptual.Formatting.Overview#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite1.vb#14)]

En plus de remplacer un élément de format par la représentation sous forme de chaîne de l'objet correspondant, les éléments de format vous permettent également de contrôler les éléments suivants :

- La façon spécifique dont un objet est représenté sous forme de chaîne, si l'objet implémente l'interface <xref:System.IFormattable> et prend en charge les chaînes de format. Ceci se fait en faisant suivre l'index de l'élément de format d'un `:` (deux-points), suivi d'une chaîne de format valide. L'exemple précédent a fait cela en mettant en forme une valeur de date avec la chaîne de format "d" (modèle de date courte) (par exemple `{0:d}`) et en mettant en forme une valeur numérique avec la chaîne de format "C2" (par exemple `{2:C2}` pour représenter le nombre comme valeur monétaire avec deux décimales.

- La largeur du champ qui contient la représentation sous forme de chaîne de l'objet, et l'alignement de la représentation sous forme de chaîne de ce champ. Ceci se fait en faisant suivre l'index de l'élément de format d'une `,` (virgule), suivie de la largeur du champ. La chaîne est alignée à droite dans le champ si la largeur du champ est une valeur positive, et elle est alignée à gauche si la largeur du champ est une valeur négative. L'exemple suivant aligne à gauche des valeurs de date dans un champ de 20 caractères, et aligne à droite des valeurs décimales avec une décimale dans un champ de 11 caractères.

     [!code-csharp[Conceptual.Formatting.Overview#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/composite2.cs#22)]
     [!code-vb[Conceptual.Formatting.Overview#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/composite2.vb#22)]

     Notez que si le composant de chaîne d'alignement et le composant de chaîne de format sont présents, le premier a priorité sur le deuxième (par exemple `{0,-20:g}`.

Pour plus d’informations sur la mise en forme composite, consultez [Composite Formatting](../../../docs/standard/base-types/composite-formatting.md).

## <a name="custom-formatting-with-icustomformatter"></a>Mise en forme personnalisée avec ICustomFormatter

Deux méthodes de mise en forme composites, <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> et <xref:System.Text.StringBuilder.AppendFormat%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, incluent également un paramètre de fournisseur de format qui prend en charge la mise en forme personnalisée. Lorsque l'une de ces méthodes de mise en forme est appelée, elle passe à la méthode <xref:System.Type> du fournisseur de format un objet <xref:System.ICustomFormatter> qui représente une interface <xref:System.IFormatProvider.GetFormat%2A> . La méthode <xref:System.IFormatProvider.GetFormat%2A> est alors chargée de retourner l'implémentation d' <xref:System.ICustomFormatter> qui fournit la mise en forme personnalisée.

L'interface <xref:System.ICustomFormatter> a une méthode unique, <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29>, qui est appelée automatiquement par une méthode de mise en forme composite, une fois pour chaque élément de mise en forme dans une chaîne de format composite. La méthode <xref:System.ICustomFormatter.Format%28System.String%2CSystem.Object%2CSystem.IFormatProvider%29> a trois paramètres : une chaîne de format, qui représente l'argument `formatString` dans un élément de mise en forme, un objet à mettre en forme et un objet <xref:System.IFormatProvider> qui fournit des services de mise en forme. En général, la classe qui implémente <xref:System.ICustomFormatter> implémente également <xref:System.IFormatProvider>; ce dernier paramètre est donc une référence à la classe de mise en forme personnalisée elle-même. La méthode retourne une représentation sous forme de chaîne mise en forme personnalisée de l'objet à mettre en forme. Si la méthode ne peut pas mettre en forme l'objet, elle doit retourner une référence null (`Nothing` en Visual Basic).

L'exemple suivant fournit une implémentation d' <xref:System.ICustomFormatter> nommée `ByteByByteFormatter` qui affiche des valeurs entières sous la forme d'une séquence de valeurs hexadécimales à deux chiffres suivie d'un espace.

[!code-csharp[Conceptual.Formatting.Overview#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#15)]
[!code-vb[Conceptual.Formatting.Overview#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#15)]

L'exemple suivant utilise la classe `ByteByByteFormatter` pour mettre en forme des valeurs entières. Notez que la méthode <xref:System.ICustomFormatter.Format%2A?displayProperty=nameWithType> est appelée plusieurs fois dans le deuxième appel de méthode <xref:System.String.Format%28System.IFormatProvider%2CSystem.String%2CSystem.Object%5B%5D%29?displayProperty=nameWithType>, et que le fournisseur <xref:System.Globalization.NumberFormatInfo> par défaut est utilisé dans le troisième appel de méthode, car la méthode .`ByteByByteFormatter.Format` ne reconnaît pas la chaîne de format "N0" et retourne une référence null (`Nothing` en Visual Basic).

[!code-csharp[Conceptual.Formatting.Overview#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.formatting.overview/cs/icustomformatter1.cs#16)]
[!code-vb[Conceptual.Formatting.Overview#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.formatting.overview/vb/icustomformatter1.vb#16)]

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Définition|
|-----------|----------------|
|[Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md)|Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées de valeurs numériques.|
|[Chaînes de format numérique personnalisées](../../../docs/standard/base-types/custom-numeric-format-strings.md)|Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les valeurs numériques.|
|[Chaînes de format de date et d'heure standard](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)|Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées de valeurs <xref:System.DateTime> .|
|[Chaînes personnalisées de format de date et d’heure](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)|Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les valeurs <xref:System.DateTime> .|
|[Chaînes de format TimeSpan standard](../../../docs/standard/base-types/standard-timespan-format-strings.md)|Décrit des chaînes de format standard qui créent des représentations sous forme de chaîne couramment utilisées d'intervalles de temps.|
|[Chaînes de format TimeSpan personnalisées](../../../docs/standard/base-types/custom-timespan-format-strings.md)|Décrit des chaînes de format personnalisées qui créent des formats spécifiques à l'application pour les intervalles de temps.|
|[Chaînes de format d’énumération](../../../docs/standard/base-types/enumeration-format-strings.md)|Décrit les chaînes de format standard qui sont utilisées pour créer des représentations sous forme de chaîne de valeurs d'énumération.|
|[Mise en forme composite](../../../docs/standard/base-types/composite-formatting.md)|Explique comment incorporer une ou plusieurs valeurs mises en forme dans une chaîne. La chaîne peut ensuite être affichée dans la console ou écrite dans un flux.|
|[Exécution d’opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)|Répertorie les rubriques qui fournissent des instructions pas à pas pour effectuer des opérations de mise en forme spécifiques.|
|[Parsing Strings](../../../docs/standard/base-types/parsing-strings.md)|Décrit comment initialiser des objets aux valeurs décrites par des représentations sous forme de chaîne de ces objets. L'analyse est l'opération inverse de la mise en forme.|

## <a name="reference"></a>Informations de référence

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.IFormatProvider?displayProperty=nameWithType>
- <xref:System.ICustomFormatter?displayProperty=nameWithType>
