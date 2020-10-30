---
title: Délégués génériques pour la manipulation de tableaux et de listes
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- delegates [.NET], generic delegates
- chaining delegates
- arrays [.NET], generic delegates
- generic delegates [.NET]
- lists [.NET], generic delegates
- generics [.NET], delegates
ms.assetid: 416be383-cc61-4102-9b1b-88b51adb963e
ms.openlocfilehash: 2ee80acb51ab3c394a3c0b12fface93a9d541f30
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063200"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Délégués génériques pour la manipulation de tableaux et de listes
Cette rubrique donne une vue d’ensemble des délégués génériques pour les conversions, des prédicats de recherche et des actions à effectuer sur les éléments d’un tableau ou d’une collection.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Délégués génériques pour la manipulation de tableaux et de listes  
 Le délégué générique <xref:System.Action%601> représente une méthode qui effectue une action sur un élément du type spécifié. Vous pouvez créer une méthode qui exécute l'action souhaitée sur l'élément, créer une instance du délégué <xref:System.Action%601> pour représenter cette méthode, puis passer le tableau et le délégué à la méthode générique statique <xref:System.Array.ForEach%2A?displayProperty=nameWithType>. La méthode est appelée pour chaque élément du tableau.  
  
 La classe générique <xref:System.Collections.Generic.List%601> fournit également une méthode <xref:System.Collections.Generic.List%601.ForEach%2A> qui utilise le délégué <xref:System.Action%601>. Cette méthode n'est pas générique.  
  
> [!NOTE]
> Ceci constitue un point intéressant concernant les types et les méthodes génériques. La méthode <xref:System.Array.ForEach%2A?displayProperty=nameWithType> doit être statique (`Shared` en Visual Basic) et générique, car <xref:System.Array> n’est pas un type générique. La seule raison pour laquelle vous pouvez spécifier un type pour que <xref:System.Array.ForEach%2A?displayProperty=nameWithType> fonctionne est que la méthode a sa propre liste de paramètres de type. En revanche, la méthode <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> non générique appartient à la classe générique <xref:System.Collections.Generic.List%601>, de sorte qu’elle utilise simplement le paramètre de type de sa classe. La classe est fortement typée :la méthode peut donc être une méthode d'instance.  
  
 Le délégué générique <xref:System.Predicate%601> représente une méthode qui détermine si un élément particulier répond aux critères que vous définissez. Vous pouvez l'utiliser avec les méthodes génériques statiques suivantes de <xref:System.Array> pour rechercher un élément ou un ensemble d'éléments : <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A> et <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601> fonctionne également avec les méthodes d'instance non génériques correspondantes de la classe générique <xref:System.Collections.Generic.List%601>.  
  
 Le délégué générique <xref:System.Comparison%601> vous permet de fournir un ordre de tri pour les éléments d'un tableau ou d'une liste qui n'ont pas un ordre de tri natif, ou de remplacer l'ordre de tri natif. Créez une méthode qui effectue la comparaison, créez une instance du délégué <xref:System.Comparison%601> pour représenter votre méthode, puis passez le tableau et le délégué à la méthode générique statique <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType>. La classe générique <xref:System.Collections.Generic.List%601> fournit une surcharge de méthode d'instance correspondante, <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 Le délégué générique <xref:System.Converter%602> vous permet de définir une conversion entre deux types et de convertir un tableau d'un type en un tableau de l'autre type, ou de convertir une liste d'un type en une liste de l'autre type. Créez une méthode qui convertit les éléments de la liste existante en un nouveau type, créez une instance de délégué pour représenter la méthode, et utilisez la méthode statique générique <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> pour générer un tableau du nouveau type à partir du tableau d'origine ou bien la méthode d'instance générique <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> pour produire une liste du nouveau type à partir de la liste d'origine.  
  
### <a name="chaining-delegates"></a>Chaînage de délégués  
 La plupart des méthodes qui utilisent ces délégués retournent un tableau ou une liste, qui peut être passé à une autre méthode. Par exemple, si vous voulez sélectionner certains éléments d'un tableau, convertir ces éléments en un nouveau type, puis les enregistrer dans un nouveau tableau, vous pouvez passer le tableau retourné par la méthode générique <xref:System.Array.FindAll%2A> à la méthode générique <xref:System.Array.ConvertAll%2A>. Si le nouveau type d'élément n'a pas un ordre de tri naturel, vous pouvez passer le tableau retourné par la méthode générique <xref:System.Array.ConvertAll%2A> à la méthode générique <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Génériques](index.md)
- [Collections génériques dans .NET](collections.md)
- [Interfaces génériques](interfaces.md)
- [Covariance et contravariance](covariance-and-contravariance.md)
