---
title: Convertir des chaînes en types
description: Comprendre l’analyse des chaînes dans .NET. L’analyse convertit une chaîne représentant un type de base .NET en ce type de base. L’analyse est l’opération inverse de la mise en forme.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 3d23fa9c7ecc3593f03f70dbd5ea7bda841e8f4f
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400851"
---
# <a name="parse-strings-in-net"></a>Analyser des chaînes dans .NET

Une opération d' *analyse* convertit une chaîne qui représente un type de base .net en ce type de base. Par exemple, une opération d’analyse est utilisée pour convertir une chaîne en nombre à virgule flottante ou en valeur de date et d’heure. La méthode la plus couramment utilisée pour effectuer une opération d’analyse est la méthode `Parse`. Étant donné que l’analyse est l’opération inverse de la mise en forme (qui consiste à convertir un type de base en sa représentation sous forme de chaîne), de nombreuses règles et conventions identiques s’appliquent. Tout comme la mise en forme utilise un objet qui implémente l’interface <xref:System.IFormatProvider> pour fournir des informations de mise en forme dépendantes de la culture, l’analyse utilise un objet qui implémente l’interface <xref:System.IFormatProvider> pour déterminer comment interpréter une représentation sous forme de chaîne. Pour plus d’informations, consultez [types de format](formatting-types.md).

## <a name="in-this-section"></a>Dans cette section
 [Analyse des chaînes numériques](parsing-numeric.md)\
 Explique comment convertir des chaînes en types numériques .NET.

 [Analyse des chaînes de date et d’heure](parsing-datetime.md)\
 Explique comment convertir des chaînes en types **DateTime** .NET.

 [Analyse d’autres chaînes](parsing-other.md)\
 Explique comment convertir des chaînes en types **Char** , **Boolean** et **Enum**.

## <a name="related-sections"></a>Sections connexes
 [Mise en forme des types](formatting-types.md)\
 Décrit les concepts de mise en forme de base, tels que les spécificateurs de format et les fournisseurs de format.

 [Conversion de type dans .NET](type-conversion.md)\
 Décrit comment convertir des types.
