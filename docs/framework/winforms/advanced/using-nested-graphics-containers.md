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
ms.openlocfilehash: 4533fbba62c36714f55cd8bd55fde7a1c8f6c9e6
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505047"
---
# <a name="using-nested-graphics-containers"></a>Utilisation de conteneurs graphiques imbriqués
GDI + fournit des conteneurs que vous pouvez utiliser pour remplacer ou augmenter la partie de l’état dans temporairement un <xref:System.Drawing.Graphics> objet. Vous créez un conteneur en appelant le <xref:System.Drawing.Graphics.BeginContainer%2A> méthode d’un <xref:System.Drawing.Graphics> objet. Vous pouvez appeler <xref:System.Drawing.Graphics.BeginContainer%2A> à plusieurs reprises pour former des conteneurs imbriqués. Chaque appel à <xref:System.Drawing.Graphics.BeginContainer%2A> doit être associé à un appel à <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
## <a name="transformations-in-nested-containers"></a>Transformations dans les conteneurs imbriqués  
 L’exemple suivant crée un <xref:System.Drawing.Graphics> objet et un conteneur dans qui <xref:System.Drawing.Graphics> objet. La transformation universelle de la <xref:System.Drawing.Graphics> objet est une translation 100 unités sur l’axe x et 80 unités dans la direction y. La transformation universelle du conteneur est une rotation de 30 degrés. Le code effectue l’appel `DrawRectangle(pen, -60, -30, 120, 60)` à deux reprises. Le premier appel à <xref:System.Drawing.Graphics.DrawRectangle%2A> est à l’intérieur du conteneur ; autrement dit, l’appel est entre les appels à <xref:System.Drawing.Graphics.BeginContainer%2A> et <xref:System.Drawing.Graphics.EndContainer%2A>. Le deuxième appel à <xref:System.Drawing.Graphics.DrawRectangle%2A> est après l’appel à <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 Dans le code précédent, le rectangle dessiné à l’intérieur du conteneur est modifié d’abord par la transformation universelle du conteneur (rotation), puis par la transformation universelle de la <xref:System.Drawing.Graphics> objet (translation). Le rectangle dessiné à l’extérieur du conteneur est transformé uniquement par la transformation universelle de la <xref:System.Drawing.Graphics> objet (translation). L’illustration suivante montre les deux rectangles : 
  
 ![Illustration des conteneurs imbriqués.](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>Découpage dans les conteneurs imbriqués  
 L’exemple suivant montre les conteneurs imbriqués comment gérer les régions de découpage. Le code crée un <xref:System.Drawing.Graphics> objet et un conteneur dans qui <xref:System.Drawing.Graphics> objet. La zone de découpage de le <xref:System.Drawing.Graphics> objet est un rectangle et la zone de découpage du conteneur est une ellipse. Le code effectue deux appels à la <xref:System.Drawing.Graphics.DrawLine%2A> (méthode). Le premier appel à <xref:System.Drawing.Graphics.DrawLine%2A> se trouve dans le conteneur et le deuxième appel à <xref:System.Drawing.Graphics.DrawLine%2A> est en dehors du conteneur (après l’appel à <xref:System.Drawing.Graphics.EndContainer%2A>). La première ligne est découpée par l’intersection des deux régions de découpage. La deuxième ligne est découpée par la région de découpage rectangulaire de la <xref:System.Drawing.Graphics> objet.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 L’illustration suivante montre les deux lignes ajustées :
  
 ![Illustration qui montre un conteneur imbriqué avec traits découpés.](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 Comme les deux exemples précédents montrent, les transformations et les régions de découpage sont cumulatifs dans des conteneurs imbriqués. Si vous définissez les transformations universelles du conteneur et le <xref:System.Drawing.Graphics> de l’objet, les deux transformations s’appliqueront aux éléments dessinés à l’intérieur du conteneur. La transformation du conteneur sera appliquée en premier et la transformation de la <xref:System.Drawing.Graphics> objet s’appliquera ensuite. Si vous définissez les régions de découpage du conteneur et le <xref:System.Drawing.Graphics> de l’objet, les éléments dessinés à l’intérieur du conteneur seront découpés par l’intersection des deux régions de découpage.  
  
## <a name="quality-settings-in-nested-containers"></a>Paramètres de qualité dans les conteneurs imbriqués  
 Paramètres de qualité (<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A>et autres) dans les conteneurs imbriqués ne sont pas cumulatifs ; au lieu de cela, les paramètres de qualité du conteneur remplacent temporairement les paramètres de qualité d’un <xref:System.Drawing.Graphics> objet. Lorsque vous créez un nouveau conteneur, les paramètres de qualité pour ce conteneur sont définis aux valeurs par défaut. Par exemple, supposons que vous ayez un <xref:System.Drawing.Graphics> objet avec le mode de lissage <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Lorsque vous créez un conteneur, le mode de lissage dans le conteneur est la valeur par défaut en mode de lissage. Vous êtes libre de définir le mode de lissage du conteneur et tous les éléments dessinés à l’intérieur du conteneur seront dessinés selon le mode que vous définissez. Éléments dessinés après l’appel à <xref:System.Drawing.Graphics.EndContainer%2A> sera dessiné selon le mode de lissage (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>) qui était en place avant l’appel à <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## <a name="several-layers-of-nested-containers"></a>Plusieurs couches de conteneurs imbriqués  
 Vous n’êtes pas limité à un conteneur dans un <xref:System.Drawing.Graphics> objet. Vous pouvez créer une séquence de conteneurs, chacun imbriqués dans l’exemple précédent, et vous pouvez spécifier la transformation universelle, zone de découpage et les paramètres de qualité de chacun de ces conteneurs imbriqués. Si vous appelez une méthode de dessin du conteneur le plus interne, les transformations sont appliquées dans l’ordre, en commençant par le conteneur le plus interne et en terminant par le conteneur le plus éloigné. Les éléments dessinés dans le conteneur le plus interne seront découpés par l’intersection de toutes les régions de découpage.  
  
 L’exemple suivant crée un <xref:System.Drawing.Graphics> de l’objet et affecte à son indicateur de rendu de texte <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Le code crée deux conteneurs, un imbriqué dans l’autre. L’indicateur de rendu de texte du conteneur externe est défini sur <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>, et l’indicateur de rendu de texte du conteneur interne est défini sur <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Le code dessine trois chaînes : une dans le conteneur interne, un dans le conteneur externe et un à partir de la <xref:System.Drawing.Graphics> objet lui-même.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 L’illustration suivante montre les trois chaînes. Les chaînes dessinées dans le conteneur interne et à partir de la <xref:System.Drawing.Graphics> objet sont lissées par l’anticrénelage. La chaîne dessinée dans le conteneur externe n’est pas lissée par l’anticrénelage car le <xref:System.Drawing.Graphics.TextRenderingHint%2A> propriété est définie sur <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![Illustration qui affiche les chaînes issues des conteneurs imbriqués.](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Graphics>
- [Gestion de l'état d'un objet graphique](managing-the-state-of-a-graphics-object.md)
