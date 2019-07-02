---
title: Métafichiers dans GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: df54289722cf12bad840722c6eafdaa43279a5dc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504587"
---
# <a name="metafiles-in-gdi"></a>Métafichiers dans GDI+
GDI + offre la <xref:System.Drawing.Imaging.Metafile> classe afin que vous pouvez enregistrer et afficher des métafichiers. Un métafichier, également appelé image vectorielle, est une image qui est stockée comme une séquence de commandes et les paramètres de dessin. Les commandes et les paramètres enregistrement dans un <xref:System.Drawing.Imaging.Metafile> objet peut être stocké en mémoire ou enregistré dans un fichier ou le flux.  
  
## <a name="metafile-formats"></a>Formats de métafichier  
 GDI + peut afficher des métafichiers qui ont été stockés dans les formats suivants :  
  
- Métafichier Windows (WMF)  
  
- métafichier amélioré (EMF)  
  
- EMF+  
  
 GDI + peut enregistrer des métafichiers aux formats EMF et EMF +, mais pas dans le format WMF.  
  
 EMF + est une extension d’EMF qui permet de stocker des enregistrements GDI +. Il existe deux variantes du format EMF + : EMF + uniquement et double EMF +. Les métafichiers EMF + Only contiennent uniquement des enregistrements GDI +. Ces métafichiers peuvent être affichés par GDI + mais pas par GDI. Les métafichiers EMF + Dual contiennent des enregistrements GDI + et GDI. Chaque enregistrement GDI + d’un métafichier EMF + Dual est associé à un autre enregistrement GDI. Ces métafichiers peuvent être affichés par GDI + ou par GDI.  
  
 L’exemple suivant affiche un métafichier précédemment enregistré en tant que fichier. Le métafichier est affiché avec son coin supérieur gauche à (100, 100).  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Voir aussi

- [Images, bitmaps et métafichiers](images-bitmaps-and-metafiles.md)
