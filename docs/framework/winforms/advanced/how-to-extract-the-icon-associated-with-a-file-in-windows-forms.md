---
title: 'Comment : extraire l’icône associée à un fichier'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 28769144b0e1c631a31c3c541747a6215f861d0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742542"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>Comment : extraire l'icône associée à un fichier dans les Windows Forms
De nombreux fichiers ont des icônes incorporées qui fournissent une représentation visuelle du type de fichier associé. Par exemple, les documents Microsoft Word contiennent une icône qui les identifie sous forme de documents Word. Lorsque vous affichez des fichiers dans un contrôle de liste ou un contrôle de table, vous pouvez afficher l’icône représentant le type de fichier en regard de chaque nom de fichier. Vous pouvez le faire facilement à l’aide de la méthode <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment extraire l’icône associée à un fichier et afficher le nom de fichier et son icône associée dans un contrôle de <xref:System.Windows.Forms.ListView>.  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour compiler l’exemple :  
  
- Collez le code précédent dans un Windows Form et appelez la méthode `ExtractAssociatedIconExample` à partir du constructeur du formulaire ou <xref:System.Windows.Forms.Form.Load> méthode de gestion d’événements.  
  
     Vous devrez vous assurer que votre formulaire importe l’espace de noms <xref:System.IO>.  
  
## <a name="see-also"></a>Voir aussi

- [Images, bitmaps et métafichiers](images-bitmaps-and-metafiles.md)
- [Contrôle ListView](../controls/listview-control-windows-forms.md)
