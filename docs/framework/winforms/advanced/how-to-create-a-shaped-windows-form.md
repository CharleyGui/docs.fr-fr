---
title: 'Procédure : créer un formulaire Windows mis en forme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], rounded
- Windows Forms, custom shapes
- Windows Forms, shaped
- shaped forms
- forms [Windows Forms], changing the shape of
- forms [Windows Forms], circular
- forms [Windows Forms], nonrectangular
- Windows Forms, nonrectangular shape
- Windows Forms, rounded
- Windows Forms, circular
- forms [Windows Forms], custom shapes
ms.assetid: 6e6041e0-8e67-4487-b1e9-e410dbd1ef6c
ms.openlocfilehash: 3c90e6d5d2613239e513f8ec30d67b58084cba5e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643496"
---
# <a name="how-to-create-a-shaped-windows-form"></a>Procédure : créer un formulaire Windows mis en forme
Cet exemple donne une forme elliptique redimensionne le formulaire à un formulaire.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[System.Drawing.ConceptualHowTos#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#10)]
 [!code-csharp[System.Drawing.ConceptualHowTos#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#10)]
 [!code-vb[System.Drawing.ConceptualHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux espaces de noms <xref:System.Windows.Forms> et <xref:System.Drawing>.  
  
 Cet exemple remplace le <xref:System.Windows.Forms.Control.OnPaint%2A> méthode pour modifier la forme du formulaire. Pour utiliser ce code, copiez la déclaration de méthode, ainsi que le code de dessin à l’intérieur de la méthode.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Drawing.Region>
- <xref:System.Drawing>
- <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>
- <xref:System.Windows.Forms.Control.Region%2A>
- [Mise en route de la programmation graphique](getting-started-with-graphics-programming.md)
