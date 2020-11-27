---
title: Marshaling de différents types de tableaux
description: Marshaler différents types de tableaux, comme des entiers par valeur ou référence, des entiers à deux dimensions par valeur, des chaînes par valeur et des structures avec des entiers ou des chaînes.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: b7777e99daf9d294bf26033f470a6e562b7b727f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269091"
---
# <a name="marshaling-different-types-of-arrays"></a>Marshaling de différents types de tableaux

Un tableau est un type référence compris dans du code managé qui contient un ou plusieurs éléments du même type. Même si les tableaux sont des types référence, ils sont passés comme des paramètres In aux fonctions non managées. Ce comportement est incohérent avec la manière dont les tableaux managés sont passés aux objets managés, c'est-à-dire en tant que paramètres In/Out. Pour plus d'informations, voir [Copie et épinglage](copying-and-pinning.md).  
  
 Le tableau suivant répertorie les options de marshaling des tableaux et décrit leur utilisation.  
  
|Array|Description|  
|-----------|-----------------|  
|D'entiers par valeur.|Passe un tableau d'entiers en tant que paramètre In.|  
|D'entiers par référence.|Passe un tableau d'entiers en tant que paramètre In/Out.|  
|D'entiers par valeur (à deux dimensions).|Passe une matrice d'entiers en tant que paramètre In.|  
|De chaînes par valeur.|Passe un tableau de chaînes en tant que paramètre In.|  
|De structures avec des entiers.|Passe un tableau de structures contenant uniquement des entiers en tant que paramètre In.|  
|De structures avec des chaînes.|Passe un tableau de structures contenant uniquement des chaînes en tant que paramètre In/Out. Les membres du tableau peuvent être modifiés.|  
  
## <a name="example"></a> Exemple  

 Cet exemple montre comment passer les types de tableaux suivants :  
  
- Tableau d'entiers par valeur.  
  
- Tableau d'entiers par référence, qui peut être redimensionné.  
  
- Tableau multidimensionnel (matrice) d'entiers par valeur.  
  
- Tableau de chaînes par valeur.  
  
- Tableau de structures avec des entiers.  
  
- Tableau de structures avec des chaînes.  
  
 À moins qu'un tableau ne soit explicitement marshalé par référence, le comportement par défaut marshale le tableau en tant que paramètre In. Vous pouvez modifier ce comportement en appliquant explicitement les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute> .  
  
 L'exemple Tableaux utilise les fonctions non managées ci-dessous, accompagnées de leur déclaration de fonction d'origine :  
  
- **TestArrayOfInts** exporté depuis PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- **TestRefArrayOfInts** exporté depuis PinvokeLib.dll.  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- **TestMatrixOfInts** exporté depuis PinvokeLib.dll.  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- **TestArrayOfStrings** exporté depuis PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- **TestArrayOfStructs** exporté depuis PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- **TestArrayOfStructs2** exporté depuis PinvokeLib.dll.  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) est une bibliothèque non managée personnalisée qui contient des implémentations pour les fonctions précédemment répertoriées, ainsi que les deux variables de structure **MYPOINT** et **MYPERSON**. Ces structures contiennent les éléments suivants :  
  
```cpp
typedef struct _MYPOINT  
{  
   int x;
   int y;
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;
   char* last;
} MYPERSON;  
```  
  
 Dans cet exemple, les structures `MyPoint` et `MyPerson` contiennent des types incorporés. L'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> est défini pour s'assurer que les membres soient disposés en mémoire de manière séquentielle, dans l'ordre dans lequel ils apparaissent.  
  
 La classe `NativeMethods` contient un ensemble de méthodes appelé par la classe `App` . Pour obtenir des détails spécifiques sur le passage de tableaux, voir les commentaires de l'exemple suivant. Un tableau, qui est un type référence, est passé en tant que paramètre par défaut. Pour que l'appelant reçoive les résultats, **InAttribute** et **OutAttribute** doivent être appliqués explicitement à l'argument contenant le tableau.  
  
### <a name="declaring-prototypes"></a>Déclaration de prototypes  

 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>Appel de fonctions  

 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Voir aussi

- [Types de données d'appel de code non managé](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Création de prototypes dans du code managé](creating-prototypes-in-managed-code.md)
