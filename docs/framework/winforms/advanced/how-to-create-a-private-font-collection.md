---
title: 'Procédure : créer une collection de polices privée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
ms.openlocfilehash: 0bb7293a5423004a13cf98b79bba0a6c411a7c97
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505516"
---
# <a name="how-to-create-a-private-font-collection"></a>Procédure : créer une collection de polices privée
Le <xref:System.Drawing.Text.PrivateFontCollection> classe hérite de la <xref:System.Drawing.Text.FontCollection> classe de base abstraite. Vous pouvez utiliser un <xref:System.Drawing.Text.PrivateFontCollection> objet pour maintenir un ensemble de polices spécifiquement pour votre application. Une collection de polices privées peut inclure des polices système installés, ainsi que des polices qui n’ont pas été installés sur l’ordinateur. Pour ajouter un fichier de polices à une collection de polices privées, appelez le <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A> méthode d’un <xref:System.Drawing.Text.PrivateFontCollection> objet.  
  
 Le <xref:System.Drawing.Text.FontCollection.Families%2A> propriété d’un <xref:System.Drawing.Text.PrivateFontCollection> objet contient un tableau de <xref:System.Drawing.FontFamily> objets.  
  
 Le nombre de familles de polices dans une collection de polices privées n’est pas nécessairement le même que le nombre de fichiers de polices qui ont été ajoutés à la collection. Par exemple, supposons que vous ajoutez les fichiers ArialBd.tff, Times.tff et TimesBd.tff à une collection. Il y aura trois fichiers mais seulement deux familles dans la collection car Times.tff et TimesBd.tff appartiennent à la même famille.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant ajoute les fichiers suivants de la trois police dans un <xref:System.Drawing.Text.PrivateFontCollection> objet :  
  
- C:\\*systemroot*\Fonts\Arial.tff (Arial, normal)  
  
- C:\\*systemroot*\Fonts\CourBI.tff (Courier New, gras et italique)  
  
- C:\\*systemroot*\Fonts\TimesBd.tff (Times New Roman, gras)  
  
 Le code récupère un tableau de <xref:System.Drawing.FontFamily> objets à partir de la <xref:System.Drawing.Text.FontCollection.Families%2A> propriété de la <xref:System.Drawing.Text.PrivateFontCollection> objet.  
  
 Pour chaque <xref:System.Drawing.FontFamily> objet dans la collection, le code appelle la <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> méthode pour déterminer si divers styles (Normal, gras, italique, gras et italique, souligné et barré) sont disponibles. Les arguments passés à la <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> méthode sont membres de la <xref:System.Drawing.FontStyle> énumération.  
  
 Si une combinaison famille/style donnée est disponible, un <xref:System.Drawing.Font> objet est construit à l’aide de cette famille et le style. Le premier argument passé à la <xref:System.Drawing.Font.%23ctor%2A> constructeur est le nom de famille de polices (pas un <xref:System.Drawing.FontFamily> comme c’est le cas pour d’autres variantes de l’objet le <xref:System.Drawing.Font.%23ctor%2A> constructeur). Après le <xref:System.Drawing.Font> objet est construit, il est passé à la <xref:System.Drawing.Graphics.DrawString%2A> méthode de la <xref:System.Drawing.Graphics> classe pour afficher le nom de famille, ainsi que le nom du style.  
  
 La sortie du code suivant est similaire à la sortie illustrée dans l’illustration suivante :  
  
 ![Capture d’écran qui affiche le texte dans des polices différentes.](./media/how-to-create-a-private-font-collection/various-fonts-text-output.png)  
  
 Arial.tff (qui a été ajouté à la collection de polices privées dans l’exemple de code suivant) est le fichier de police pour le style Arial regular. Toutefois, notez que la sortie du programme montre plusieurs styles disponibles autres que standard pour la famille de polices Arial. C’est parce que GDI + peut simuler les styles italique, gras et italiques et gras depuis le style Normal. GDI + peut également produire des soulignements et barrés depuis le style Normal.  
  
 De même, GDI + peut simuler le style gras et italique à partir du style gras ou italique. La sortie du programme montre que le style italique gras est disponible pour la famille de fois bien que TimesBd.tff (Times New Roman, gras) est le seul fichier fois dans la collection.  
  
 [!code-csharp[System.Drawing.FontsAndText#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Text.PrivateFontCollection>
- [Utilisation de polices et de texte](using-fonts-and-text.md)
