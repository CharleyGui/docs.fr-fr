---
title: Valeurs numériques dans .NET
ms.date: 10/18/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- SIMD
- System.Numerics.Vectors
- vectors
- scientific computing
- Complex
- numerics
- BigInteger
ms.assetid: dfebc18e-acde-4510-9fa7-9a0f4aa3bd11
ms.openlocfilehash: 3b95a322377e82249a0375af589df74c658fcbf4
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507414"
---
# <a name="numerics-in-net"></a>Valeurs numériques dans .NET

.NET fournit une plage de primitives numériques pour les intégraux et les nombres à virgule flottante, ainsi que <xref:System.Numerics.BigInteger?displayProperty=nameWithType>, un type intégral sans limite théorique supérieure ou inférieure, <xref:System.Numerics.Complex?displayProperty=nameWithType>, qui représente des nombres complexes et un ensemble de types compatibles SIMD dans l’espace de noms <xref:System.Numerics>.
  
## <a name="integer-types"></a>Types d'entier

.NET prend en charge à la fois les types d’entier signés et non signés 8, 16, 32 et 64 bits, répertoriés dans le tableau suivant :
  
|Type|Signé/Non signé|Taille (en octets)|Valeur minimale|Valeur maximale|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|Non signé|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|Signé|2|-32,768|32 767|  
|<xref:System.Int32?displayProperty=nameWithType>|Signé|4|-2,147,483,648|2 147 483 647|  
|<xref:System.Int64?displayProperty=nameWithType>|Signé|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|Signé|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|Non signé|2|0|65 535|  
|<xref:System.UInt32?displayProperty=nameWithType>|Non signé|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|Non signé|8|0|18 446 744 073 709 551 615|  
  
Chaque type d’entier prend en charge un ensemble d’opérateurs arithmétiques standard. La classe <xref:System.Math?displayProperty=nameWithType> fournit des méthodes pour un ensemble plus large de fonctions mathématiques.

Vous pouvez également travailler avec les bits individuels d'une valeur d'entier en utilisant la classe <xref:System.BitConverter?displayProperty=nameWithType>.  

> [!NOTE]  
> Les types d’entier non signés ne sont pas conformes à CLS. Pour plus d'informations, consultez [Language Independence and Language-Independent Components](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

La structure <xref:System.Numerics.BigInteger?displayProperty=nameWithType> est un type immuable qui représente un entier arbitrairement grand dont la valeur en théorie n'a pas de limite supérieure ou inférieure. Les méthodes du type <xref:System.Numerics.BigInteger> sont très proches de celles des autres types intégraux.
  
## <a name="floating-point-types"></a>Types virgule flottante

.NET comprend trois types à virgule flottante primitifs, qui sont répertoriés dans le tableau suivant :
  
|Type|Taille (en octets)|Plage approximative|Precision|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|±1,5 x 10<sup>−45</sup> à ±3,4 x 10<sup>38</sup>|~6-9 chiffres|  
|<xref:System.Double?displayProperty=nameWithType>|8|De ±5,0 × 10<sup>−324</sup> à ±1,7 × 10<sup>308</sup>|~15-17 chiffres|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|±1,0 x 10<sup>-28</sup> to ±7,9228 x 10<sup>28</sup>|28 à 29 chiffres|  
  
Les deux types <xref:System.Single> et <xref:System.Double> prennent en charge des valeurs spéciales qui représentent une valeur NaN (N’est pas un nombre) et l’infini. Par exemple, le type <xref:System.Double> fournit les valeurs suivantes : <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> et <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>. Vous utilisez les méthodes <xref:System.Double.IsNaN%2A?displayProperty=nameWithType>, <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>, <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType> et <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> pour tester ces valeurs spéciales.

Chaque type à virgule flottante prend en charge un ensemble d’opérateurs arithmétiques standard. La classe <xref:System.Math?displayProperty=nameWithType> fournit des méthodes pour un ensemble plus large de fonctions mathématiques. .NET Core 2,0 et versions ultérieures <xref:System.MathF?displayProperty=nameWithType> incluent la classe, qui fournit des méthodes qui acceptent <xref:System.Single> des arguments du type.

Vous pouvez également travailler avec les bits individuels de valeurs <xref:System.Double> et <xref:System.Single> en utilisant la classe <xref:System.BitConverter?displayProperty=nameWithType>. La structure <xref:System.Decimal?displayProperty=nameWithType> a ses propres méthodes, <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> et <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29> pour travailler avec les bits individuel d'une valeur décimale, ainsi que son propre ensemble de méthodes pour effectuer d'autres opérations mathématiques.
  
Les <xref:System.Double> types <xref:System.Single> et sont destinés à être utilisés pour les valeurs qui, par nature, sont imprécises (par exemple, la distance entre deux étoiles) et pour les applications dans lesquelles un degré élevé de précision et une erreur d’arrondi réduite ne sont pas requis. Utilisez le <xref:System.Decimal?displayProperty=nameWithType> type pour les cas où une plus grande précision est nécessaire et où les erreurs d’arrondi doivent être réduites.

> [!NOTE]
> Le type <xref:System.Decimal> n’élimine pas la nécessité d’arrondi. Au lieu de cela, il réduit les erreurs dues à l’arrondi.
  
## <a name="complex"></a>Complex

La structure <xref:System.Numerics.Complex?displayProperty=nameWithType> représente un nombre complexe, c'est-à-dire un nombre avec une partie réelle et une partie imaginaire. Elle prend en charge un ensemble standard d'opérateurs arithmétiques, de comparaison, d'égalité, de conversion explicite et implicite, ainsi que des méthodes mathématiques, algébriques et trigonométriques.  
  
## <a name="simd-enabled-types"></a>Types SIMD

L’espace de noms <xref:System.Numerics> comprend un ensemble de types compatibles SIMD pour .NET. Les opérations SIMD (Single Instruction Multiple Data) peuvent être parallélisées au niveau du matériel. Cela augmente le débit des calculs vectorisés, couramment utilisés dans les applications mathématiques, scientifiques et graphiques.
  
Les types .NET compatibles SIMD sont les suivants :

- Les types <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3> et <xref:System.Numerics.Vector4>, qui représentent des vecteurs à 2, 3 et 4 valeurs <xref:System.Single>.

- Deux types de matrices, <xref:System.Numerics.Matrix3x2>, qui représente une matrice 3 x 2, et <xref:System.Numerics.Matrix4x4>, qui représente une matrice 4 x 4.

- Le type <xref:System.Numerics.Plane>, qui représente un plan dans un espace à trois dimensions.

- Le type <xref:System.Numerics.Quaternion>, qui représente un vecteur utilisé pour encoder des rotations physiques en trois dimensions.

- Le type <xref:System.Numerics.Vector%601>, qui représente un vecteur d’un type numérique spécifié et fournit un large éventail d’opérateurs bénéficiant d’un support SIMD. Le nombre d’une instance <xref:System.Numerics.Vector%601> est fixe, mais sa valeur <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> dépend de l’UC de l’ordinateur sur lequel le code est exécuté.
  > [!NOTE]
  > Le type <xref:System.Numerics.Vector%601> n’est pas inclus dans .NET Framework. Vous devez installer le package NuGet [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) pour accéder à ce type.
  
Les types compatibles SIMD sont implémentés de telle sorte qu’ils peuvent être utilisés avec du matériel non compatible SIMD ou des compilateurs JIT. Pour tirer parti des instructions SIMD, vos applications 64 bits doivent être exécutées par le runtime qui utilise le compilateur RyuJIT, inclus dans .NET Core et dans .NET Framework 4.6 et versions ultérieures. Il ajoute la prise en charge SIMD lors du ciblage de processeurs 64 bits.

Pour plus d’informations, consultez [utiliser des types numériques SIMD accélérés](simd.md).

## <a name="see-also"></a>Voir aussi

- [Chaînes de format numériques standard](base-types/standard-numeric-format-strings.md)
