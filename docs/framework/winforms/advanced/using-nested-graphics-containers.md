---
title: Utilisation de conteneurs graphiques imbriqués
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
ms.openlocfilehash: 460ebb37ee62691a1e282f756840121fd378ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182465"
---
# <a name="using-nested-graphics-containers"></a>Utilisation de conteneurs graphiques imbriqués
GDIMD fournit des conteneurs que vous pouvez utiliser pour <xref:System.Drawing.Graphics> remplacer ou augmenter temporairement une partie de l’état dans un objet. Vous créez un conteneur <xref:System.Drawing.Graphics.BeginContainer%2A> en <xref:System.Drawing.Graphics> appelant la méthode d’un objet. Vous pouvez <xref:System.Drawing.Graphics.BeginContainer%2A> appeler à plusieurs reprises pour former des conteneurs imbriqués. Chaque appel <xref:System.Drawing.Graphics.BeginContainer%2A> doit être jumelé à <xref:System.Drawing.Graphics.EndContainer%2A>un appel à .  
  
## <a name="transformations-in-nested-containers"></a>Transformations dans les conteneurs imbriqués  
 L’exemple suivant <xref:System.Drawing.Graphics> crée un objet <xref:System.Drawing.Graphics> et un conteneur à l’intérieur de cet objet. La transformation du <xref:System.Drawing.Graphics> monde de l’objet est une traduction de 100 unités dans la direction x et 80 unités dans la direction y. La transformation mondiale du conteneur est une rotation de 30 degrés. Le code fait `DrawRectangle(pen, -60, -30, 120, 60)` l’appel deux fois. Le premier <xref:System.Drawing.Graphics.DrawRectangle%2A> appel est à l’intérieur du conteneur; c’est-à-dire, l’appel est entre les appels à <xref:System.Drawing.Graphics.BeginContainer%2A> et <xref:System.Drawing.Graphics.EndContainer%2A>. Le deuxième <xref:System.Drawing.Graphics.DrawRectangle%2A> appel à est <xref:System.Drawing.Graphics.EndContainer%2A>après l’appel à .  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 Dans le code précédent, le rectangle tiré de l’intérieur du récipient est transformé d’abord <xref:System.Drawing.Graphics> par la transformation du monde du conteneur (rotation) puis par la transformation du monde de l’objet (traduction). Le rectangle tiré de l’extérieur du récipient <xref:System.Drawing.Graphics> n’est transformé que par la transformation mondiale de l’objet (traduction). L’illustration suivante montre les deux rectangles :
  
 ![Illustration qui montre des conteneurs imbriqués.](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>Clipping dans des conteneurs imbriqués  
 L’exemple suivant montre comment les conteneurs imbriqués gèrent les régions de coupure. Le code <xref:System.Drawing.Graphics> crée un objet <xref:System.Drawing.Graphics> et un conteneur à l’intérieur de cet objet. La région de <xref:System.Drawing.Graphics> coupure de l’objet est un rectangle, et la région de coupure du récipient est une ellipse. Le code passe deux <xref:System.Drawing.Graphics.DrawLine%2A> appels à la méthode. Le premier <xref:System.Drawing.Graphics.DrawLine%2A> appel à est à l’intérieur du conteneur, et le deuxième appel à est à l’extérieur <xref:System.Drawing.Graphics.DrawLine%2A> du conteneur (après l’appel à <xref:System.Drawing.Graphics.EndContainer%2A>). La première ligne est coupée par l’intersection des deux régions de coupure. La deuxième ligne n’est coupée que par la <xref:System.Drawing.Graphics> région rectangulaire de coupe de l’objet.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 L’illustration suivante montre les deux lignes coupées :
  
 ![Illustration qui montre un récipient imbriqué avec des lignes coupées.](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 Comme le montrent les deux exemples précédents, les transformations et les régions de coupure sont cumulatives dans les conteneurs imbriqués. Si vous définissez les transformations <xref:System.Drawing.Graphics> mondiales du conteneur et de l’objet, les deux transformations s’appliqueront aux éléments tirés de l’intérieur du conteneur. La transformation du conteneur sera appliquée en premier, et la transformation de l’objet <xref:System.Drawing.Graphics> sera appliquée en second lieu. Si vous définissez les régions <xref:System.Drawing.Graphics> de coupure du conteneur et de l’objet, les objets tirés de l’intérieur du conteneur seront coupés par l’intersection des deux régions de coupure.  
  
## <a name="quality-settings-in-nested-containers"></a>Paramètres de qualité dans les conteneurs imbriqués  
 Les paramètres<xref:System.Drawing.Graphics.SmoothingMode%2A> <xref:System.Drawing.Graphics.TextRenderingHint%2A>de qualité (, , et autres) dans les conteneurs imbriqués ne sont pas cumulatifs; les paramètres de qualité du conteneur remplacent <xref:System.Drawing.Graphics> temporairement les paramètres de qualité d’un objet. Lorsque vous créez un nouveau conteneur, les paramètres de qualité de ce conteneur sont définis selon des valeurs par défaut. Par exemple, supposons <xref:System.Drawing.Graphics> que vous avez <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>un objet avec un mode de lissage de . Lorsque vous créez un conteneur, le mode de lissage à l’intérieur du conteneur est le mode de lissage par défaut. Vous êtes libre de définir le mode de lissage du conteneur, et tous les articles tirés de l’intérieur du conteneur seront dessinés selon le mode que vous définissez. Les objets dessinés <xref:System.Drawing.Graphics.EndContainer%2A> après l’appel seront tirés selon le mode de lissage ()<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>qui était en place avant l’appel à <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## <a name="several-layers-of-nested-containers"></a>Plusieurs couches de conteneurs imbriqués  
 Vous n’êtes pas limité <xref:System.Drawing.Graphics> à un conteneur dans un objet. Vous pouvez créer une séquence de conteneurs, chacun niché dans le précédent, et vous pouvez spécifier la transformation du monde, la région de coupure, et les paramètres de qualité de chacun de ces conteneurs imbriqués. Si vous appelez une méthode de dessin de l’intérieur du récipient le plus intérieur, les transformations seront appliquées dans l’ordre, en commençant par le récipient le plus intérieur et se terminant par le récipient le plus externe. Les articles tirés de l’intérieur du conteneur le plus intime seront coupés par l’intersection de toutes les régions de coupure.  
  
 L’exemple suivant <xref:System.Drawing.Graphics> crée un objet et <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>définit son indice de rendu de texte à . Le code crée deux conteneurs, l’un imbriqué dans l’autre. Le soupçon de rendu de texte <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>du récipient externe est réglé à, et <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>le soupçon de rendu de texte du récipient intérieur est réglé à . Le code dessine trois cordes : une du récipient intérieur, une <xref:System.Drawing.Graphics> du récipient extérieur et une de l’objet lui-même.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 L’illustration suivante montre les trois cordes. Les cordes tirées du récipient <xref:System.Drawing.Graphics> intérieur et de l’objet sont lissées par l’antianage. La ficelle tirée du récipient extérieur n’est pas <xref:System.Drawing.Graphics.TextRenderingHint%2A> lissée <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>par l’antialiasing parce que la propriété est réglée à .  
  
 ![Illustration qui montre les cordes tirées de récipients imbriqués.](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Graphics>
- [Gestion de l'état d'un objet graphique](managing-the-state-of-a-graphics-object.md)
