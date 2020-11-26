---
title: MsgBox, exemple
description: Consultez un exemple de passage de types chaîne par valeurs comme paramètres in à l’aide de MsgBox. Il indique quand utiliser les champs EntryPoint, CharSet et ExactSpelling dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
ms.openlocfilehash: 024ed612115ce73646596651fe454238418446db
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242017"
---
# <a name="msgbox-sample"></a>MsgBox, exemple

Cet exemple montre comment passer des types chaîne par valeur comme paramètres entrants, et quand utiliser les champs <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> et <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>.  
  
 L’exemple MsgBox utilise la fonction non managée suivante, accompagnée de sa déclaration de fonction d’origine :  
  
- **MessageBox** exportée depuis User32.dll.  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 Dans cet exemple, la classe `NativeMethods` contient un prototype managé pour chaque fonction non managée appelée par la classe `MsgBoxSample`. Les méthodes du prototype managé `MsgBox`, `MsgBox2` et `MsgBox3` ont des déclarations différentes pour la même fonction non managée.  
  
 La déclaration pour `MsgBox2` produit un résultat incorrect dans la boîte de message, car le type de caractère, spécifié comme étant ANSI, ne correspond pas au point d’entrée de `MessageBoxW`, qui est le nom de la fonction Unicode. La déclaration pour `MsgBox3` crée une non-correspondance entre les champs **EntryPoint**, **CharSet** et **ExactSpelling**. Quand elle est appelée, `MsgBox3` lève une exception. Pour plus d’informations sur le nommage des chaînes et le marshaling des noms, consultez [Spécification d’un jeu de caractères](specifying-a-character-set.md).  
  
## <a name="declaring-prototypes"></a>Déclaration de prototypes  

 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a>Appel de fonctions  

 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Marshaling de chaînes](marshaling-strings.md)
- [Marshaling par défaut pour les chaînes](default-marshaling-for-strings.md)
- [Création de prototypes dans du code managé](creating-prototypes-in-managed-code.md)
- [Spécification d'un jeu de caractères](specifying-a-character-set.md)
