---
title: Analyse de chaînes dans .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: e4bf14981e538d95aebac3b0f36d38b61747989f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084315"
---
# <a name="parsing-strings-in-net"></a>Analyse de chaînes dans .NET
Une opération d’analyse convertit une chaîne qui représente un type de base .NET en ce type de base. Par exemple, une opération d'analyse permet de convertir une chaîne en nombre à virgule flottante ou en valeur de date et d'heure. La méthode la plus couramment utilisée pour effectuer une opération d’analyse est la méthode `Parse`. Étant donné que l’analyse est l’opération inverse de la mise en forme (qui consiste à convertir un type de base en sa représentation sous forme de chaîne), de nombreuses règles et conventions identiques s’appliquent. Tout comme la mise en forme utilise un objet qui implémente l’interface <xref:System.IFormatProvider> pour fournir des informations de mise en forme dépendantes de la culture, l’analyse utilise un objet qui implémente l’interface <xref:System.IFormatProvider> pour déterminer comment interpréter une représentation sous forme de chaîne. Pour plus d’informations, consultez [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Analyse de chaînes numériques](../../../docs/standard/base-types/parsing-numeric.md)  
 Explique comment convertir des chaînes en types numériques .NET.  
  
 [Analyse de chaînes de date et d’heure](../../../docs/standard/base-types/parsing-datetime.md)  
 Explique comment convertir des chaînes en types **DateTime** .NET.  
  
 [Analyse d’autres chaînes](../../../docs/standard/base-types/parsing-other.md)  
 Explique comment convertir des chaînes en types **Char**, **Boolean** et **Enum**.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)  
 Décrit les concepts de mise en forme de base, tels que les spécificateurs de format et les fournisseurs de format.  
  
 [Conversion de type dans .NET](../../../docs/standard/base-types/type-conversion.md)  
 Décrit comment convertir des types.  
  
 [Types de base](../../../docs/standard/base-types/index.md)  
 Décrit les opérations courantes que vous pouvez effectuer sur les types de base .NET.
