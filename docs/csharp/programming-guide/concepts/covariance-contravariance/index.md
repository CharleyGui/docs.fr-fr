---
title: Covariance et contravariance (C#)
description: En savoir plus sur la covariance et la contravariance et sur la manière dont elles affectent la compatibilité des affectations. Consultez un exemple de code qui illustre les différences entre eux.
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: 65c75029c27b6c9a5ddc96f01622b520e8698f55
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105695"
---
# <a name="covariance-and-contravariance-c"></a>Covariance et contravariance (C#)
En C#, la covariance et la contravariance permettent la conversion de références implicite pour les types tableau, les types délégués et les arguments de type générique. La covariance conserve la compatibilité d’assignation et la contravariance l’inverse.  
  
 Le code suivant illustre la différence entre la compatibilité d’assignation, la covariance et la contravariance.  
  
```csharp  
// Assignment compatibility.
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.
object obj = str;  
  
// Covariance.
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument
// is assigned to an object instantiated with a less derived type argument.
// Assignment compatibility is preserved.
IEnumerable<object> objects = strings;  
  
// Contravariance.
// Assume that the following method is in the class:
// static void SetObject(object o) { }
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument
// is assigned to an object instantiated with a more derived type argument.
// Assignment compatibility is reversed.
Action<string> actString = actObject;  
```  
  
 La covariance pour les tableaux permet la conversion implicite d’un tableau d’un type plus dérivé en un tableau d’un type moins dérivé. Cette opération n’est cependant pas sécurisée au niveau des types, comme le montre l’exemple de code suivant.  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 La prise en charge de la covariance et la contravariance pour les groupes de méthodes permet la correspondance des signatures de méthode avec des types délégués. Ceci vous permet d’affecter aux délégués non seulement les méthodes ayant des signatures correspondantes, mais aussi des méthodes qui retournent des types plus dérivés (covariance) ou qui acceptent des paramètres ayant des types moins dérivés (contravariance) que ceux spécifiés par le type délégué. Pour plus d’informations, consultez [Variance dans les délégués (C#)](./variance-in-delegates.md) et [Utilisation de la variance dans les délégués (C#)](./using-variance-in-delegates.md).  
  
 L’exemple de code suivant montre la prise en charge de la covariance et de la contravariance pour les groupes de méthode.  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 Dans .NET Framework 4 et versions ultérieures, C# prend en charge la covariance et la contravariance dans les interfaces et les délégués génériques, et permet la conversion implicite de paramètres de type générique. Pour plus d’informations, consultez [Variance dans les interfaces génériques (C#)](./variance-in-generic-interfaces.md) et [Variance dans les délégués (C#)](./variance-in-delegates.md).  
  
 L’exemple de code suivant illustre la conversion de références implicite pour les interfaces génériques.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Une interface ou un délégué générique est dit de type *variant* si ses paramètres génériques sont déclarés covariants ou contravariants. C# vous permet de créer vos propres interfaces et délégués de type variant. Pour plus d’informations, consultez [Création d’interfaces génériques de type variant (C#)](./creating-variant-generic-interfaces.md) et [Variance dans les délégués (C#)](./variance-in-delegates.md).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Variance dans les interfaces génériques (C#)](./variance-in-generic-interfaces.md)|Décrit la covariance et la contravariance dans les interfaces génériques et fournit la liste des interfaces génériques de type variant dans le .NET Framework.|  
|[Création d’interfaces génériques de type variant (C#)](./creating-variant-generic-interfaces.md)|Montre comment créer des interfaces de type variant personnalisées.|  
|[Utilisation de la variance dans les interfaces pour les collections génériques (C#)](./using-variance-in-interfaces-for-generic-collections.md)|Montre comment la prise en charge de la covariance et de la contravariance dans les interfaces <xref:System.Collections.Generic.IEnumerable%601> et <xref:System.IComparable%601> peut vous aider à réutiliser du code.|  
|[Variance dans les délégués (C#)](./variance-in-delegates.md)|Présente la covariance et la contravariance dans les délégués génériques et non génériques, et fournit une liste des délégués génériques de type variant dans le .NET Framework.|  
|[Utilisation de la variance dans les délégués (C#)](./using-variance-in-delegates.md)|Montre comment utiliser la prise en charge de la covariance et de la contravariance dans les délégués non génériques pour faire correspondre des signatures de méthode avec des types délégués.|  
|[Utilisation de la variance pour les délégués génériques Func et Action (C#)](./using-variance-for-func-and-action-generic-delegates.md)|Montre comment la prise en charge de la covariance et de la contravariance dans les délégués `Func` et `Action` peut vous aider à réutiliser du code.|
