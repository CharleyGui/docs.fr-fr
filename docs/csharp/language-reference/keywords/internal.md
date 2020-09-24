---
description: internal - Référence C#
title: internal - Référence C#
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: c66f4ff578e9864ebaf2b89ec03ce95f3cb2ba91
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168736"
---
# <a name="internal-c-reference"></a>internal (référence C#)

Le mot clé `internal` est un [modificateur d’accès](./access-modifiers.md) pour les types et les membres de type.
  
 > Cette page traite de l’accès `internal`. Le `internal` mot clé fait également partie du [`protected internal`](./protected-internal.md) modificateur d’accès.
  
Les types et les membres internes (internal) sont accessibles uniquement dans les fichiers d’un même assembly, comme dans l’exemple suivant :  
  
```csharp  
public class BaseClass
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 Pour obtenir une comparaison de `internal` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](./accessibility-levels.md) et [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md).  
  
 Pour plus d'informations sur les assemblys, consultez [Aassemblys dans .NET](../../../standard/assembly/index.md).  
  
 L’accès interne est fréquemment utilisé lors du développement basé sur les composants, car il permet à un groupe de composants de collaborer de façon privée sans être exposés au reste du code de l’application. Par exemple, un framework de création d’interfaces graphiques utilisateur peut fournir les classes `Control` et `Form` qui coopèrent en utilisant des membres ayant un accès interne. Étant donné que ces membres sont internes, ils ne sont pas exposés au code qui utilise le framework.  
  
 Le fait de référencer un type ou un membre avec accès interne en dehors de l’assembly dans lequel il a été défini constitue une erreur.  
  
## <a name="example"></a>Exemple  

 Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly1_a.cs`. Le premier fichier contient la classe de base interne `BaseClass`. Dans le deuxième fichier, une tentative d’instanciation de `BaseClass` génère une erreur.  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess
{  
   static void Main()
   {  
      var myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a>Exemple  

 Dans cet exemple, utilisez les mêmes fichiers que vous avez utilisés dans l’exemple 1, et remplacez le niveau d’accessibilité `BaseClass` par `public`. Remplacez également le niveau d’accessibilité du membre `intM` par `internal`. Dans ce cas, vous pouvez instancier la classe, mais vous ne pouvez pas accéder au membre interne.  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly2.dll  
public class TestAccess
{  
   static void Main()
   {  
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Accessibilité déclarée](~/_csharplang/spec/basic-concepts.md#declared-accessibility) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](./index.md)
- [Modificateurs d’accès](./access-modifiers.md)
- [Niveaux d'accessibilité](./accessibility-levels.md)
- [Modificateurs](index.md)
- [public](./public.md)
- [priv](./private.md)
- [protected](./protected.md)
