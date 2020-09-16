---
title: types blittable et non blittable
description: En savoir plus sur les types blittables et non blittables. Les types de données blittables sont communément représentés dans la mémoire managée et non managée et n’ont pas besoin d’un traitement spécial.
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
ms.openlocfilehash: 8bbf9c72143033cec22b38cc26cbe8ceb44f790b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556269"
---
# <a name="blittable-and-non-blittable-types"></a>types blittable et non blittable
La plupart des types de données ont une représentation commune à la fois dans la mémoire managée et non managée, et ne nécessitent pas de traitement particulier par le marshaleur d’interopérabilité. Ces types sont appelés *types blittables*, car ils ne nécessitent pas de conversion quand ils transitent entre le code managé et le code non managé.  
  
 Les structures qui sont retournées par les appels de code non managé doivent être des types blittables. L’appel de code non managé ne prend en charge aucune structure non blittable comme type de retour.  
  
 Les types suivants issus de l’espace de noms <xref:System> sont des types blittables :  
  
- <xref:System.Byte?displayProperty=nameWithType>  
  
- <xref:System.SByte?displayProperty=nameWithType>  
  
- <xref:System.Int16?displayProperty=nameWithType>  
  
- <xref:System.UInt16?displayProperty=nameWithType>  
  
- <xref:System.Int32?displayProperty=nameWithType>  
  
- <xref:System.UInt32?displayProperty=nameWithType>  
  
- <xref:System.Int64?displayProperty=nameWithType>  
  
- <xref:System.UInt64?displayProperty=nameWithType>  
  
- <xref:System.IntPtr?displayProperty=nameWithType>  
  
- <xref:System.UIntPtr?displayProperty=nameWithType>  
  
- <xref:System.Single?displayProperty=nameWithType>  
  
- <xref:System.Double?displayProperty=nameWithType>  
  
 Les types complexes suivants sont également des types blittables :  
  
- Tableaux unidimensionnels de types blittables, comme un tableau d’entiers. Toutefois, un type qui contient un tableau de variables de types blittables n’est pas lui-même blittable.  
  
- Types valeur mis en forme qui ne contiennent que des types blittables (et des classes s’ils sont marshalés comme types mis en forme). Pour plus d’informations sur les types valeur mis en forme, consultez [Marshaling par défaut pour les types valeur](default-marshaling-behavior.md#default-marshaling-for-value-types).  
  
 Les références d’objets ne sont pas blittables. Cela inclut un tableau de références aux objets qui sont blittables en eux-mêmes. Par exemple, vous pouvez définir une structure blittable, mais vous ne pouvez pas définir un type blittable contenant un tableau de références à ces structures.  
  
 Par souci d’optimisation, les tableaux de types et de classes blittables qui ne contiennent que des membres blittables sont [épinglés](copying-and-pinning.md) au lieu d’être copiés lors du marshaling. Ces types semblent être marshalés en tant que paramètres en entrée/sortie quand l’appelant et l’appelé résident dans le même cloisonnement. Cependant, ces types sont en fait marshalés en tant que paramètres en entrée et vous devez appliquer les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute> si vous voulez marshaler l’argument en tant que paramètre en entrée/sortie.  
  
 Certains types de données managés requièrent une représentation différente dans un environnement non managé. Ces types de données non blittables doivent être convertis sous une forme qui peut être marshalée. Par exemple, les chaînes managées sont des types non blittables parce qu’elles doivent être converties en objets String avant de pouvoir être marshalées.  
  
 Le tableau suivant répertorie des types non blittables issus de l’espace de noms <xref:System>. Les [délégués](default-marshaling-behavior.md#default-marshaling-for-delegates), qui sont des structures de données qui réfèrent à une méthode statique ou à une instance de classe, sont également non blittables.  
  
|Type non blittable|Description|  
|-------------------------|-----------------|  
|[System.Array](default-marshaling-for-arrays.md)|Convertit en tableau de style C ou en `SAFEARRAY`.|  
|[System.Boolean](/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))|Convertit en valeur de 1, 2 ou 4 octets, la valeur `true` ayant pour valeur 1 ou -1.|  
|[System.Char](/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))|Convertit en caractère ANSI ou Unicode.|  
|[System.Class](/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))|Convertit en interface de classe.|  
|[System.Object](default-marshaling-for-objects.md)|Convertit en interface ou en variant.|  
|[System.Mdarray](default-marshaling-for-arrays.md)|Convertit en tableau de style C ou en `SAFEARRAY`.|  
|[System.String](default-marshaling-for-strings.md)|Convertit en chaîne se terminant par une référence null ou en BSTR.|  
|[System.Valuetype](/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))|Convertit en structure avec une disposition de mémoire fixe.|  
|[System.Szarray](default-marshaling-for-arrays.md)|Convertit en tableau de style C ou en `SAFEARRAY`.|  
  
 Les types d’objets et de classes sont pris en charge uniquement par COM Interop. Pour obtenir les types correspondants en Visual Basic, C# et C++, consultez [Vue d’ensemble de la bibliothèque de classes .NET Framework](../../standard/class-library-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [comportement de marshaling par défaut](default-marshaling-behavior.md)
