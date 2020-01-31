---
title: Fonctions mathématiques
ms.date: 01/27/2020
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: ea30ae3b30484c1a13d6d540f121c03afb30ba26
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794593"
---
# <a name="math-functions-visual-basic"></a>Fonctions mathématiques (Visual Basic)

Les méthodes de la classe <xref:System.Math?displayProperty=nameWithType> fournissent des fonctions trigonométriques, logarithmiques et d’autres fonctions mathématiques courantes.

## <a name="remarks"></a>Notes

Le tableau suivant répertorie les méthodes de la classe <xref:System.Math?displayProperty=nameWithType>. Vous pouvez les utiliser dans un programme Visual Basic :
  
|Méthode .NET|Description|
|---------------------------|-----------------|
|<xref:System.Math.Abs%2A>|Retourne la valeur absolue d'un nombre.|
|<xref:System.Math.Acos%2A>|Retourne l'angle dont le cosinus est le nombre spécifié.|
|<xref:System.Math.Asin%2A>|Retourne l'angle dont le sinus est le nombre spécifié.|
|<xref:System.Math.Atan%2A>|Retourne l'angle dont la tangente est le nombre spécifié.|
|<xref:System.Math.Atan2%2A>|Retourne l'angle dont la tangente est le quotient de deux nombres spécifiés.|
|<xref:System.Math.BigMul%2A>|Retourne le produit complet de nombres 2 32 bits.|
|<xref:System.Math.Ceiling%2A>|Retourne la plus petite valeur intégrale qui est supérieure ou égale à la `Decimal` ou à la `Double`spécifiée.|
|<xref:System.Math.Cos%2A>|Retourne le cosinus de l'angle spécifié.|
|<xref:System.Math.Cosh%2A>|Retourne le cosinus hyperbolique de l'angle spécifié.|
|<xref:System.Math.DivRem%2A>|Retourne le quotient d’entiers signés 2 32 bits ou 64 bits, et retourne également le reste dans un paramètre de sortie.|
|<xref:System.Math.Exp%2A>|Retourne e (la base des logarithmes naturels) élevée à la puissance spécifiée.|
|<xref:System.Math.Floor%2A>|Retourne le plus grand entier qui est inférieur ou égal au nombre `Decimal` ou `Double` spécifié.|
|<xref:System.Math.IEEERemainder%2A>|Retourne le reste qui résulte de la Division d’un nombre spécifié par un autre nombre spécifié.|
|<xref:System.Math.Log%2A>|Retourne le logarithme népérien (base e) d’un nombre spécifié ou le logarithme d’un nombre spécifié dans une base spécifiée.|
|<xref:System.Math.Log10%2A>|Retourne le logarithme de base 10 d'un nombre spécifié.|
|<xref:System.Math.Max%2A>|Retourne le plus grand de deux nombres.|
|<xref:System.Math.Min%2A>|Retourne le plus petit de deux nombres.|
|<xref:System.Math.Pow%2A>|Retourne un nombre spécifié élevé à la puissance spécifiée.|
|<xref:System.Math.Round%2A>|Retourne une valeur `Decimal` ou `Double` arrondie à la valeur intégrale la plus proche ou à un nombre spécifié de chiffres fractionnaires.|
|<xref:System.Math.Sign%2A>|Retourne une valeur `Integer` qui indique le signe d’un nombre.|
|<xref:System.Math.Sin%2A>|Retourne le sinus de l'angle spécifié.|
|<xref:System.Math.Sinh%2A>|Retourne le sinus hyperbolique de l'angle spécifié.|
|<xref:System.Math.Sqrt%2A>|Retourne la racine carrée d'un nombre spécifié.|
|<xref:System.Math.Tan%2A>|Retourne la tangente de l'angle spécifié.|
|<xref:System.Math.Tanh%2A>|Retourne la tangente hyperbolique de l'angle spécifié.|
|<xref:System.Math.Truncate%2A>|Calcule la partie entière d’un `Decimal` ou d’un nombre de `Double` spécifié.|

Le tableau suivant répertorie les méthodes de la classe <xref:System.Math?displayProperty=nameWithType> qui n’existent pas dans .NET Framework mais qui sont ajoutées à .NET Standard ou à .NET Core :

|Méthode .NET|Description|Disponible dans|
|---------------------------|-----------------|-----------|
|<xref:System.Math.Acosh%2A>|Retourne l'angle dont le cosinus hyperbolique est le nombre spécifié.|À compter de .NET Core 2,1 et .NET Standard 2,1|
|<xref:System.Math.Asinh%2A>|Retourne l’angle dont le sinus hyperbolique est le nombre spécifié.|À compter de .NET Core 2,1 et .NET Standard 2,1|
|<xref:System.Math.Atanh%2A>|Retourne l’angle dont la tangente hyperbolique est le nombre spécifié.|À compter de .NET Core 2,1 et .NET Standard 2,1|
|<xref:System.Math.BitDecrement%2A>|Retourne la plus petite valeur suivante qui est inférieure à `x`.|À compter de .NET Core 3,0|
|<xref:System.Math.BitIncrement%2A>|Retourne la plus grande valeur suivante qui est supérieure à `x`.|À compter de .NET Core 3,0|
|<xref:System.Math.Cbrt%2A>|Retourne la racine cubique d’un nombre spécifié.|À compter de .NET Core 2,1 et .NET Standard 2,1|
|<xref:System.Math.Clamp%2A>|Retourne `value`, valeur limitée à la plage inclusive `min`-`max`.|À compter de .NET Core 2,0 et .NET Standard 2,1|
|<xref:System.Math.CopySign%2A>|Retourne une valeur d’amplitude `x` et de signe `y`.|À compter de .NET Core 3,0|
|<xref:System.Math.FusedMultiplyAdd%2A>|Retourne (x \* y) + z, arrondi comme une opération ternaire.|À compter de .NET Core 3,0|
|<xref:System.Math.ILogB%2A>|Retourne le logarithme entier de base 2 d’un nombre spécifié.|À compter de .NET Core 3,0|
|<xref:System.Math.Log2%2A>|Retourne le logarithme de base 2 d’un nombre spécifié.|À compter de .NET Core 3,0|
|<xref:System.Math.MaxMagnitude%2A>|Retourne la plus grande amplitude de deux nombres à virgule flottante double précision.|À compter de .NET Core 3,0|
|<xref:System.Math.MinMagnitude%2A>|Retourne la plus petite amplitude de deux nombres à virgule flottante double précision.|À compter de .NET Core 3,0|
|<xref:System.Math.ScaleB%2A>|Retourne x \* 2 ^ n calculé efficacement.|À compter de .NET Core 3,0|

Pour utiliser ces fonctions sans qualification, importez l’espace de noms <xref:System.Math?displayProperty=nameWithType> dans votre projet en ajoutant le code suivant au début de votre fichier source :

```vb
Imports System.Math
```

## <a name="example---abs"></a>Exemple-ABS

Cet exemple utilise la méthode <xref:System.Math.Abs%2A> de la classe <xref:System.Math> pour calculer la valeur absolue d’un nombre.

```vb
Dim x As Double = Math.Abs(50.3)
Dim y As Double = Math.Abs(-50.3)
Console.WriteLine(x)
Console.WriteLine(y)
' This example produces the following output:
' 50.3
' 50.3
```  

## <a name="example---atan"></a>Exemple-atan

Cet exemple utilise la méthode <xref:System.Math.Atan%2A> de la classe <xref:System.Math> pour calculer la valeur de pi.

```vb
Public Function GetPi() As Double
    ' Calculate the value of pi.
    Return 4.0 * Math.Atan(1.0)
End Function
```

> [!NOTE]
> La classe <xref:System.Math?displayProperty=nameWithType> contient <xref:System.Math.PI?displayProperty=nameWithType> champ de constante. Vous pouvez l’utiliser au lieu de le calculer.

## <a name="example---cos"></a>Exemple-COS

Cet exemple utilise la méthode <xref:System.Math.Cos%2A> de la classe <xref:System.Math> pour retourner le cosinus d’un angle.

```vb
Public Function Sec(angle As Double) As Double
    ' Calculate the secant of angle, in radians.
    Return 1.0 / Math.Cos(angle)
End Function
```

## <a name="example---exp"></a>Exemple-exp

Cet exemple utilise la méthode <xref:System.Math.Exp%2A> de la classe <xref:System.Math> pour retourner e élevé à une puissance.

```vb
Public Function Sinh(angle As Double) As Double
    ' Calculate hyperbolic sine of an angle, in radians.
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0
End Function
```

## <a name="example---log"></a>Exemple-Journal

Cet exemple utilise la méthode <xref:System.Math.Log%2A> de la classe <xref:System.Math> pour retourner le logarithme népérien d’un nombre.

```vb
Public Function Asinh(value As Double) As Double
    ' Calculate inverse hyperbolic sine, in radians.
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))
End Function
```

## <a name="example---round"></a>Exemple-Round

Cet exemple utilise la méthode <xref:System.Math.Round%2A> de la classe <xref:System.Math> pour arrondir un nombre à l’entier le plus proche.

```vb
Dim myVar2 As Double = Math.Round(2.8)
Console.WriteLine(myVar2)
' The code produces the following output:
' 3
```

## <a name="example---sign"></a>Exemple-Sign

Cet exemple utilise la méthode <xref:System.Math.Sign%2A> de la classe <xref:System.Math> pour déterminer le signe d’un nombre.

```vb
Dim mySign1 As Integer = Math.Sign(12)
Dim mySign2 As Integer = Math.Sign(-2.4)
Dim mySign3 As Integer = Math.Sign(0)
Console.WriteLine(mySign1)
Console.WriteLine(mySign2)
Console.WriteLine(mySign3)
' The code produces the following output:
' 1
' -1
' 0
```

## <a name="example---sin"></a>Exemple-Sin

Cet exemple utilise la méthode <xref:System.Math.Sin%2A> de la classe <xref:System.Math> pour retourner le sinus d’un angle.

```vb
Public Function Csc(angle As Double) As Double
    ' Calculate cosecant of an angle, in radians.
    Return 1.0 / Math.Sin(angle)
End Function
```

## <a name="example---sqrt"></a>Exemple : sqrt

Cet exemple utilise la méthode <xref:System.Math.Sqrt%2A> de la classe <xref:System.Math> pour calculer la racine carrée d’un nombre.

```vb
Dim mySqrt1 As Double = Math.Sqrt(4)
Dim mySqrt2 As Double = Math.Sqrt(23)
Dim mySqrt3 As Double = Math.Sqrt(0)
Dim mySqrt4 As Double = Math.Sqrt(-4)
Console.WriteLine(mySqrt1)
Console.WriteLine(mySqrt2)
Console.WriteLine(mySqrt3)
Console.WriteLine(mySqrt4)
' The code produces the following output:
' 2
' 4.79583152331272
' 0
' NaN
```

## <a name="example---tan"></a>Exemple-Tan

Cet exemple utilise la méthode <xref:System.Math.Tan%2A> de la classe <xref:System.Math> pour retourner la tangente d’un angle.

```vb
Public Function Ctan(angle As Double) As Double
    ' Calculate cotangent of an angle, in radians.
    Return 1.0 / Math.Tan(angle)
End Function
```

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>
- <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>
- <xref:System.Double.NaN>
- [Fonctions mathématiques dérivées](../keywords/derived-math-functions.md)
- [Opérateurs arithmétiques](../operators/arithmetic-operators.md)
