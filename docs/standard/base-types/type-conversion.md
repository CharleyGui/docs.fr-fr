---
title: Conversion de type dans le .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- widening conversions
- explicit conversions
- narrowing conversions
- type conversion, about type conversion
- type conversion
- converting types
- narrowing coercion
- Explicit operator
- IConvertible interface
- base types, converting
- op_Implicit method
- widening coercion
- op_Explicit method
- Convert class
- implicit conversions
- Implicit operator
- data types [.NET Framework], converting
ms.assetid: ba36154f-064c-47d3-9f05-72f93a7ca96d
ms.openlocfilehash: 33b8c49033c901917e674879048558799f484194
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291654"
---
# <a name="type-conversion-in-the-net-framework"></a>Conversion de type dans le .NET Framework
Chaque valeur a un type associé qui définit des attributs, tels la quantité d'espace allouée à la valeur, la plage de valeurs possibles et les membres qu'il rend disponibles. De nombreuses valeurs peuvent être exprimées sous forme de plusieurs types. Par exemple, la valeur 4 peut être exprimée sous forme d'un entier ou d'une valeur à virgule flottante. La conversion de type crée une valeur dans un nouveau type qui est équivalente à la valeur d'un ancien type, mais ne préserve pas nécessairement l'identité (ou la valeur exacte) de l'objet d'origine.  
  
 Le .NET Framework prend automatiquement en charge les conversions suivantes :  
  
- Conversion d’une classe dérivée vers une classe de base. Cela signifie, par exemple, qu’une instance d’une classe ou d’une structure peut être convertie en instance <xref:System.Object>.  Cette conversion ne nécessite pas d’opérateur de conversion ou de cast.  
  
- Reconversion d’une classe de base vers la classe dérivée d’origine. En C#, cette conversion nécessite un opérateur de cast. En Visual Basic, elle nécessite l’opérateur `CType` si `Option Strict` est activée.  
  
- Conversion d’un type qui implémente une interface vers un objet d’interface qui représente cette interface. Cette conversion ne nécessite pas d’opérateur de conversion ou de cast.  
  
- Reconversion d’un objet d’interface vers le type d’origine qui implémente cette interface.  En C#, cette conversion nécessite un opérateur de cast. En Visual Basic, elle nécessite l’opérateur `CType` si `Option Strict` est activée.  
  
 En plus de ces conversions automatiques, .NET Framework fournit plusieurs fonctionnalités qui prennent en charge la conversion personnalisée. Ces options en question sont les suivantes :  
  
- L'opérateur `Implicit`, qui définit les conversions étendues disponibles entre des types. Pour plus d’informations, consultez la section [conversion implicite avec l’opérateur Implicit](#implicit-conversion-with-the-implicit-operator) .  
  
- L'opérateur `Explicit`, qui définit les conversions restrictives entre des types. Pour plus d’informations, consultez la section [conversion explicite avec l’opérateur Explicit](#explicit-conversion-with-the-explicit-operator) .  
  
- L'interface <xref:System.IConvertible>, qui définit des conversions vers chacun des types de données .NET Framework de base. Pour plus d’informations, consultez la section [Interface IConvertible](#the-iconvertible-interface).  
  
- La classe <xref:System.Convert>, qui fournit un ensemble de méthodes qui implémentent les méthodes dans l'interface <xref:System.IConvertible>. Pour plus d’informations, consultez la section [Classe Convert](#the-convert-class).  
  
- La classe <xref:System.ComponentModel.TypeConverter>, qui est une classe de base qui peut être étendue pour prendre en charge la conversion d'un type spécifié vers un autre type. Pour plus d’informations, consultez la section [Classe TypeConverter](#the-typeconverter-class).  

## <a name="implicit-conversion-with-the-implicit-operator"></a>Conversion implicite avec l'opérateur Implicit  
 Les conversions étendues impliquent la création d'une valeur à partir de la valeur d'un type existant dont la plage est plus restrictive ou qui contient une liste de membres plus restreinte que le type cible. Les conversions étendues ne peuvent pas entraîner de perte de données (bien qu'elles puissent produire un résultat de moindre précision). Étant donné qu'aucune donnée ne peut être perdue, les compilateurs peuvent gérer la conversion de façon implicite ou transparente, sans exiger l'utilisation d'une méthode de conversion explicite ou d'un opérateur de cast.  
  
> [!NOTE]
> Même si le code qui exécute une conversion implicite peut appeler une méthode de conversion ou utiliser un opérateur de cast, son utilisation n'est pas requise par les compilateurs qui prennent en charge les conversions implicites.  
  
 Par exemple, le type <xref:System.Decimal> prend en charge les conversions implicites à partir des valeurs <xref:System.Byte>, <xref:System.Char>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.UInt16>, <xref:System.UInt32> et <xref:System.UInt64>. L'exemple suivant illustre certaines de ces conversions implicites en assignant des valeurs à une variable <xref:System.Decimal>.  
  
 [!code-csharp[Conceptual.Conversion#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#1)]
 [!code-vb[Conceptual.Conversion#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#1)]  
  
 Si un compilateur de langage particulier prend en charge des opérateurs personnalisés, vous pouvez également définir des conversions implicites dans vos propres types personnalisés. L'exemple suivant fournit une implémentation partielle d'un type de données d'octets signés nommé `ByteWithSign` qui utilise la représentation « signe et magnitude ». Il prend en charge la conversion implicite des valeurs <xref:System.Byte> et <xref:System.SByte> en valeurs `ByteWithSign`.  
  
 [!code-csharp[Conceptual.Conversion#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#2)]
 [!code-vb[Conceptual.Conversion#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#2)]  
  
 Le code client peut ensuite déclarer une variable `ByteWithSign` et lui assigner les valeurs <xref:System.Byte> et <xref:System.SByte> sans exécuter de conversion explicite ni utiliser d'opérateur de cast, comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[Conceptual.Conversion#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/implicit1.cs#3)]
 [!code-vb[Conceptual.Conversion#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/implicit1.vb#3)]  

## <a name="explicit-conversion-with-the-explicit-operator"></a>Conversion explicite avec l'opérateur Explicit  
 Les conversions restrictives impliquent la création d'une valeur à partir de la valeur d'un type existant dont la plage est plus étendue ou qui contient une liste de membres plus étendue que le type cible. Une conversion restrictive pouvant entraîner une perte de données, les compilateurs exigent souvent que la conversion soit effectuée de façon implicite via un appel à une méthode de conversion ou à un opérateur de cast. En d'autres termes, la conversion doit être gérée de manière explicite dans le code du développeur.  
  
> [!NOTE]
> Exiger une méthode de conversion ou un opérateur de cast pour les conversions restrictives a pour principal objectif que le développeur soit conscient des risques de perte de données ou d'un <xref:System.OverflowException> et puisse les gérer dans le code. Toutefois, certains compilateurs peuvent assouplir cette exigence. Par exemple, en Visual Basic, si `Option Strict` est désactivé (paramètre par défaut), le compilateur Visual Basic essaie d'exécuter des conversions restrictives de manière implicite.  
  
 Par exemple, les types de données <xref:System.UInt32>, <xref:System.Int64> et <xref:System.UInt64> ont tous des plages qui dépassent celle du type de données <xref:System.Int32>, comme indiqué dans le tableau suivant.  
  
|Type|Comparaison avec la plage de Int32|  
|----------|------------------------------------|  
|<xref:System.Int64>|<xref:System.Int64.MaxValue?displayProperty=nameWithType> est supérieur à <xref:System.Int32.MaxValue?displayProperty=nameWithType> et <xref:System.Int64.MinValue?displayProperty=nameWithType> est inférieur à (a une plage négative supérieure à) <xref:System.Int32.MinValue?displayProperty=nameWithType>.|  
|<xref:System.UInt32>|<xref:System.UInt32.MaxValue?displayProperty=nameWithType> est supérieur à <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
|<xref:System.UInt64>|<xref:System.UInt64.MaxValue?displayProperty=nameWithType> est supérieur à <xref:System.Int32.MaxValue?displayProperty=nameWithType>.|  
  
 Pour gérer ces conversions restrictives, .NET Framework permet aux types de définir un opérateur `Explicit`. Chaque compilateur de langage peut ensuite implémenter cet opérateur à l'aide de sa propre syntaxe, ou un membre de la classe <xref:System.Convert> peut être appelé pour effectuer la conversion. (Pour plus d’informations sur la <xref:System.Convert> classe, consultez [la classe Convert](#the-convert-class) plus loin dans cette rubrique.) L’exemple suivant illustre l’utilisation de fonctionnalités de langage pour gérer la conversion explicite de ces valeurs entières potentiellement hors limites en <xref:System.Int32> valeurs.  
  
 [!code-csharp[Conceptual.Conversion#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#4)]
 [!code-vb[Conceptual.Conversion#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#4)]  
  
 Les conversions explicites peuvent produire des résultats différents selon les langages, et ces résultats peuvent différer de la valeur retournée par la méthode <xref:System.Convert> correspondante. Par exemple, si la valeur <xref:System.Double> 12.63251 est convertie en <xref:System.Int32>, la méthode `CInt` Visual Basic et la méthode <xref:System.Convert.ToInt32%28System.Double%29?displayProperty=nameWithType> .NET Framework arrondissent toutes les deux <xref:System.Double> pour retourner la valeur 13, mais l'opérateur `(int)` C# tronque <xref:System.Double> pour retourner la valeur 12. De la même façon, l'opérateur `(int)` C# ne prend pas en charge la conversion de données booléennes en entier, mais la méthode `CInt` Visual Basic convertit la valeur `true` en -1. En revanche, la méthode <xref:System.Convert.ToInt32%28System.Boolean%29?displayProperty=nameWithType> convertit la valeur `true` en 1.  
  
 La plupart des compilateurs autorisent les conversions explicites contrôlées ou non contrôlées. Lorsqu'une conversion contrôlée est effectuée, un <xref:System.OverflowException> est levé lorsque la valeur du type à convertir se situe hors de la plage du type cible. Lorsqu'une conversion non contrôlée est effectuée dans les mêmes circonstances, la conversion n'entraîne pas nécessairement la levée d'une exception, mais le comportement exact devient indéfini et la valeur obtenue peut être incorrecte.  
  
> [!NOTE]
> En C#, vous pouvez effectuer des conversions contrôlées à l'aide du mot clé `checked` et d'un opérateur de cast, ou en spécifiant l'option de compilateur `/checked+`. Vous pouvez également effectuer des conversions non contrôlées à l'aide du mot clé `unchecked` et de l'opérateur de cast ou en spécifiant l'option de compilateur `/checked-`. Par défaut, les conversions explicites ne sont pas contrôlées. Dans Visual Basic, vous pouvez effectuer des conversions contrôlées en désactivant la case à cocher **Supprimer les contrôles de dépassement sur les entiers** dans la boîte de dialogue **Paramètres avancés du compilateur** du projet ou en spécifiant l’option de compilateur `/removeintchecks-`. En revanche, pour effectuer des conversions non contrôlées, activez la case à cocher **Supprimer les contrôles de dépassement sur les entiers** dans la boîte de dialogue **Paramètres avancés du compilateur** du projet, ou spécifiez l’option de compilateur `/removeintchecks+`. Par défaut, les conversions explicites sont contrôlées.  
  
 L'exemple C# suivant utilise les mots clés `checked` et `unchecked` pour illustrer la différence de comportement lorsqu'une valeur en dehors de la plage d'un <xref:System.Byte> est convertie en <xref:System.Byte>. La conversion contrôlée lève une exception, mais la conversion non contrôlée assigne <xref:System.Byte.MaxValue?displayProperty=nameWithType> à la variable <xref:System.Byte>.  
  
 [!code-csharp[Conceptual.Conversion#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#12)]  
  
 Si un compilateur de langage particulier prend en charge des opérateurs surchargés personnalisés, vous pouvez également définir des conversions explicites dans vos propres types personnalisés. L'exemple suivant fournit une implémentation partielle d'un type de données d'octets signés nommé `ByteWithSign` qui utilise la représentation « signe et magnitude ». Il prend en charge la conversion explicite des valeurs <xref:System.Int32> et <xref:System.UInt32> en valeurs `ByteWithSign`.  
  
 [!code-csharp[Conceptual.Conversion#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#5)]
 [!code-vb[Conceptual.Conversion#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#5)]  
  
 Le code client peut ensuite déclarer une variable `ByteWithSign` et lui assigner les valeurs <xref:System.Int32> et <xref:System.UInt32> si les assignations incluent un opérateur de cast ou une méthode de conversion, comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[Conceptual.Conversion#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/explicit1.cs#6)]
 [!code-vb[Conceptual.Conversion#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/explicit1.vb#6)]  

## <a name="the-iconvertible-interface"></a>Interface IConvertible  
 Pour prendre en charge la conversion de n’importe quel type vers un type de base du Common Language Runtime (CLR), .NET Framework fournit l’interface <xref:System.IConvertible>. Le type d'implémentation est requis pour fournir les éléments suivants :  
  
- une méthode qui retourne le <xref:System.TypeCode> du type d'implémentation ;  
  
- des méthodes pour convertir le type d'implémentation vers chacun des types de base Common Language Runtime (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, etc.) ;  
  
- une méthode de conversion généralisée pour convertir une instance du type d'implémentation dans un autre type spécifié. Les conversions qui ne sont pas prises en charge doivent lever un <xref:System.InvalidCastException>.  
  
 Chacun des types de base Common Language Runtime (c'est-à-dire, <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.String>, <xref:System.UInt16>, <xref:System.UInt32> et <xref:System.UInt64>), ainsi que les types <xref:System.DBNull> et <xref:System.Enum> implémentent l'interface <xref:System.IConvertible>. Il s'agit toutefois d'implémentations d'interface explicites. La méthode de conversion ne peut être appelée que via une variable d'interface <xref:System.IConvertible>, comme le montre l'exemple suivant. Cet exemple convertit une valeur <xref:System.Int32> en sa valeur <xref:System.Char> équivalente.  
  
 [!code-csharp[Conceptual.Conversion#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible1.cs#7)]
 [!code-vb[Conceptual.Conversion#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible1.vb#7)]  
  
 L’exigence visant à appeler la méthode de conversion sur son interface plutôt que sur le type d’implémentation rend les implémentations d’interface explicites relativement coûteuse. En lieu et place, nous vous recommandons d'appeler le membre approprié de la classe <xref:System.Convert> pour effectuer des conversions entre des types de base Common Language Runtime. Pour plus d’informations, consultez la section suivante, [classe Convert](#the-convert-class).  
  
> [!NOTE]
> Outre l’interface <xref:System.IConvertible> et la classe <xref:System.Convert> fournies par .NET Framework, chaque langage peut également offrir des moyens d’effectuer des conversions. Par exemple, C# utilise des opérateurs de casting et Visual Basic fait appel à des fonctions de conversion implémentées par compilateur, telles que `CType`, `CInt` et `DirectCast`.  
  
 L’interface <xref:System.IConvertible> est en grande partie conçue pour prendre en charge la conversion entre les types de base dans .NET Framework. Toutefois, l'interface peut également être implémentée par un type personnalisé pour prendre en charge la conversion de ce type vers d'autres types personnalisés. Pour plus d’informations, consultez la section [conversions personnalisées avec la méthode ChangeType](#custom-conversions-with-the-changetype-method) , plus loin dans cette rubrique.

## <a name="the-convert-class"></a>Classe Convert
 L'implémentation de l'interface <xref:System.IConvertible> de chaque type de base peut être appelée pour effectuer une conversion de type. Toutefois, l'appel des méthodes de la classe <xref:System.Convert?displayProperty=nameWithType> est recommandé pour effectuer une conversion d'un type de base vers un autre, car il est indépendant du langage. Par ailleurs, la méthode <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> peut être utilisée pour convertir un type personnalisé spécifié vers un autre type.  
  
### <a name="conversions-between-base-types"></a>Conversions entre types de base  
 La classe <xref:System.Convert> constitue une façon indépendante du langage d'effectuer des conversions entre des types de base, et est disponible pour tous les langages qui ciblent le Common Language Runtime (CLR). Elle fournit un ensemble complet de méthodes pour les conversions étendues et restrictives, et lève un <xref:System.InvalidCastException> pour les conversions qui ne sont pas prises en charge (telles que la conversion d'une valeur <xref:System.DateTime> en valeur entière). Les conversions restrictives sont effectuées dans un contexte vérifié (checked), et un <xref:System.OverflowException> est levé en cas d'échec de la conversion.  
  
> [!IMPORTANT]
> Étant donné que la classe <xref:System.Convert> inclut des méthodes permettant d'effectuer des conversions pour chaque type de base, elle évite de devoir appeler l'implémentation d'interface explicite <xref:System.IConvertible> de chaque type de base.  
  
 L'exemple suivant illustre l'utilisation de la classe <xref:System.Convert?displayProperty=nameWithType> pour effectuer plusieurs conversions étendues et restrictives entre des types de base du .NET Framework.  
  
 [!code-csharp[Conceptual.Conversion#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#8)]
 [!code-vb[Conceptual.Conversion#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#8)]  
  
 Dans certains cas, particulièrement lors de la conversion entre des valeurs à virgule flottante, une conversion peut impliquer une perte de précision, bien qu'elle ne lève pas d'<xref:System.OverflowException>. L'exemple suivant illustre cette perte de précision. Dans le premier cas, une valeur <xref:System.Decimal> a moins de précision (moins de chiffres significatifs) lorsqu'elle est convertie en <xref:System.Double>. Dans le second cas, une valeur <xref:System.Double> est arrondie de 42,72 à 43 afin de terminer la conversion.  
  
 [!code-csharp[Conceptual.Conversion#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/convert1.cs#9)]
 [!code-vb[Conceptual.Conversion#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/convert1.vb#9)]  
  
 Pour obtenir un tableau qui répertorie les conversions étendues et restrictives prises en charge par la classe <xref:System.Convert>, consultez [Tableaux de conversion de types](conversion-tables.md).  

### <a name="custom-conversions-with-the-changetype-method"></a>Conversions personnalisées avec la méthode ChangeType  
 Outre la prise en charge des conversions vers chacun des types de base, la classe <xref:System.Convert> peut être utilisée pour convertir un type personnalisé vers un ou plusieurs types prédéfinis. Cette conversion est effectuée par la méthode <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, qui inclut ensuite dans un wrapper un appel à la méthode <xref:System.IConvertible.ToType%2A?displayProperty=nameWithType> du paramètre `value`. Ainsi, l'objet représenté par le paramètre `value` doit fournir une implémentation de l'interface <xref:System.IConvertible>.  
  
> [!NOTE]
> Étant donné que les méthodes <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%29?displayProperty=nameWithType> et <xref:System.Convert.ChangeType%28System.Object%2CSystem.Type%2CSystem.IFormatProvider%29?displayProperty=nameWithType> utilisent un objet <xref:System.Type> pour spécifier le type de cible vers lequel la `value` est convertie, elles peuvent être utilisées pour réaliser une conversion dynamique vers un objet dont le type n'est pas connu au moment de la compilation. Cependant, notez que l'implémentation de <xref:System.IConvertible> de la `value` doit toujours prendre en charge cette conversion.  
  
 L'exemple suivant illustre une implémentation possible de l'interface <xref:System.IConvertible> qui permet de convertir un objet `TemperatureCelsius` en objet `TemperatureFahrenheit`, et inversement. Cet exemple définit une classe de base, `Temperature`, qui implémente l'interface <xref:System.IConvertible> et substitue la méthode <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Les classes dérivées `TemperatureCelsius` et `TemperatureFahrenheit` substituent chacune les méthodes `ToType` et `ToString` de la classe de base.  
  
 [!code-csharp[Conceptual.Conversion#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#10)]
 [!code-vb[Conceptual.Conversion#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#10)]  
  
 L'exemple suivant illustre plusieurs appels à ces implémentations de <xref:System.IConvertible> pour convertir des objets `TemperatureCelsius` en objets `TemperatureFahrenheit`, et inversement.  
  
 [!code-csharp[Conceptual.Conversion#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.conversion/cs/iconvertible2.cs#11)]
 [!code-vb[Conceptual.Conversion#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.conversion/vb/iconvertible2.vb#11)]  

## <a name="the-typeconverter-class"></a>Classe TypeConverter  
 Grâce au .NET Framework, vous pouvez également définir un convertisseur de type pour un type personnalisé en étendant la classe <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType> et en associant le convertisseur de type au type grâce à un attribut <xref:System.ComponentModel.TypeConverterAttribute?displayProperty=nameWithType>. Le tableau suivant met en évidence les différences entre cette approche et l'implémentation de l'interface <xref:System.IConvertible> pour un type personnalisé.  
  
> [!NOTE]
> La prise en charge au moment du design ne peut être fournie pour un type personnalisé que si un convertisseur de type est défini pour ce dernier.  
  
|Conversion à l'aide de TypeConverter|Conversion à l'aide de IConvertible|  
|------------------------------------|-----------------------------------|  
|Est implémentée pour un type personnalisé en dérivant une classe distincte de <xref:System.ComponentModel.TypeConverter>. Cette classe dérivée est associée au type personnalisé en appliquant un attribut <xref:System.ComponentModel.TypeConverterAttribute>.|Est implémentée par un type personnalisé pour effectuer la conversion. Un utilisateur du type appelle une méthode de conversion <xref:System.IConvertible> sur le type.|  
|Peut être utilisée à la fois au moment du design et au moment de l'exécution.|Ne peut être utilisée qu'au moment de l'exécution.|  
|Utilise la réflexion, et est donc plus lente que la conversion à l'aide de <xref:System.IConvertible>.|N'utilise pas la réflexion.|  
|Permet les conversions de type bilatérales du type personnalisé en d'autres types de données, et d'autres types de données en type personnalisé. Par exemple, un <xref:System.ComponentModel.TypeConverter> défini pour `MyType` permet d'effectuer des conversions de `MyType` en <xref:System.String>, et de <xref:System.String> en `MyType`.|Permet la conversion d'un type personnalisé en d'autres types de données, mais pas d'autres types de données en type personnalisé.|  
  
 Pour plus d'informations sur l'utilisation de convertisseurs de type pour effectuer des conversions, consultez <xref:System.ComponentModel.TypeConverter?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.IConvertible>
- [Tables de conversion de type](conversion-tables.md)
