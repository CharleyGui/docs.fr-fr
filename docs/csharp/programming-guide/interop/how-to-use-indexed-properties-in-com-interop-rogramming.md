---
title: 'Procédure : Utiliser des propriétés indexées dans la programmation COM Interop - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: f1be14ad7ddb6973cc89f10c1735ba2ebce13f97
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971647"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Procédure : Utiliser des propriétés indexées dans la programmation COM Interop (Guide de programmation C#)
Les *propriétés indexées* améliorent la façon dont les propriétés COM avec des paramètres sont consommées dans la programmation C#. Les propriétés indexées fonctionnent avec d’autres fonctionnalités dans Visual C#, comme les [arguments nommés et facultatifs](../classes-and-structs/named-and-optional-arguments.md), un nouveau type ([dynamique](../../language-reference/keywords/dynamic.md)) et [les informations de type incorporées](../../../standard/assembly/embed-types-visual-studio.md), pour améliorer la programmation Microsoft Office.  
  
 Dans les versions antérieures de C#, les méthodes sont accessibles comme des propriétés uniquement si la méthode `get` n’a aucun paramètre et que la méthode `set` a un seul et unique paramètre de valeur. Toutefois, toutes les propriétés COM ne respectent pas ces restrictions. Par exemple, la propriété <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> d’Excel a un accesseur `get`, qui nécessite un paramètre pour le nom de la plage. Dans le passé, parce que vous ne pouviez pas accéder à la propriété `Range` directement, vous deviez utiliser la méthode `get_Range` à la place, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Les propriétés indexées vous permettent d’écrire ce qui suit à la place :  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> L’exemple précédent utilise également la fonctionnalité des [arguments facultatifs](../classes-and-structs/named-and-optional-arguments.md), qui vous permet d’omettre `Type.Missing`.  
  
 De même, pour définir la valeur de la propriété `Value` d’un objet <xref:Microsoft.Office.Interop.Excel.Range> dans C# 3.0 et les versions antérieures, deux arguments sont nécessaires. L’un fournit un argument pour un paramètre facultatif qui spécifie le type de la valeur de la plage. L’autre fournit la valeur de la propriété `Value`. Les exemples suivants illustrent ces techniques. Les deux définissent la valeur de la cellule A1 sur `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Les propriétés indexées vous permettent d’écrire le code suivant à la place.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Vous ne pouvez pas créer vos propres propriétés indexées. La fonctionnalité prend uniquement en charge la consommation de propriétés indexées existantes.  
  
## <a name="example"></a>Exemples  
 L'exemple de code suivant illustre l'exemple complet. Pour plus d’informations sur la configuration d’un projet qui accède à l’API Office, consultez [Guide pratique pour accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#](./how-to-access-office-onterop-objects.md).  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Voir aussi

- [Arguments nommés et facultatifs](../classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../language-reference/keywords/dynamic.md)
- [Utilisation du type dynamic](../types/using-type-dynamic.md)
- [Guide pratique : utiliser des arguments nommés et facultatifs dans la programmation Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Guide pratique : accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#](./how-to-access-office-onterop-objects.md)
- [Procédure pas à pas : programmation Office](./walkthrough-office-programming.md)
