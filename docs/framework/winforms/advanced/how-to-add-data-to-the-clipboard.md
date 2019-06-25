---
title: 'Procédure : ajouter des données au Presse-papiers'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: 06ce64de5e2a6b4aa299b9ad9c41982b7c1924c7
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348273"
---
# <a name="how-to-add-data-to-the-clipboard"></a>Procédure : ajouter des données au Presse-papiers
Le <xref:System.Windows.Forms.Clipboard> classe fournit des méthodes que vous pouvez utiliser pour interagir avec la fonctionnalité de Presse-papiers du système d’exploitation Windows. De nombreuses applications utilisent le Presse-papiers comme référentiel temporaire pour les données. Par exemple, les traitements de texte utiliser le Presse-papiers lors des opérations de couper-coller. Le Presse-papiers est également utile pour transférer des données d’une application vers un autre.  
  
 Lorsque vous ajoutez des données dans le Presse-papiers, vous pouvez indiquer le format de données afin que les autres applications puissent reconnaître les données lorsqu’elles peuvent utiliser ce format. Vous pouvez également ajouter des données dans le Presse-papiers dans plusieurs formats différents pour augmenter le nombre d’autres applications qui peut utiliser les données.  
  
 Un format de Presse-papiers est une chaîne qui identifie le format afin qu’une application qui utilise ce format peut récupérer les données associées. Le <xref:System.Windows.Forms.DataFormats> classe fournit les noms de formats prédéfinis pour votre usage. Vous pouvez également utiliser vos propres noms de format, ou utiliser le type d’un objet comme son format.  
  
 Pour ajouter des données dans le Presse-papiers dans un ou plusieurs formats, utilisez le <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> (méthode). Vous pouvez passer n’importe quel objet à cette méthode, mais pour ajouter des données dans plusieurs formats, vous devez d’abord ajouter les données à un objet distinct conçu pour fonctionner avec plusieurs formats. En règle générale, vous allez ajouter vos données à un <xref:System.Windows.Forms.DataObject>, mais vous pouvez utiliser n’importe quel type qui implémente le <xref:System.Windows.Forms.IDataObject> interface.  
  
 Dans .NET Framework 2.0, vous pouvez ajouter des données directement dans le Presse-papiers à l’aide de nouvelles méthodes conçues pour simplifier les tâches de base du Presse-papiers. Utilisez ces méthodes lorsque vous travaillez avec des données dans un format commun unique telles que du texte.  
  
> [!NOTE]
>  Toutes les applications basées sur Windows partagent le Presse-papiers. Par conséquent, le contenu est susceptible de changer lorsque vous basculez vers une autre application.  
>   
>  Le <xref:System.Windows.Forms.Clipboard> classe peut uniquement être utilisée dans les threads en mode de thread unique cloisonné (STA). Pour utiliser cette classe, vérifiez que votre `Main` méthode est marquée avec le <xref:System.STAThreadAttribute> attribut.  
>   
>  Un objet doit être sérialisable être placé dans le Presse-papiers. Pour rendre un type sérialisable, marquez-le avec le <xref:System.SerializableAttribute> attribut. Si vous passez un objet non sérialisable à une méthode de Presse-papiers, la méthode échoue sans lever d’exception. Pour plus d'informations sur la sérialisation, consultez <xref:System.Runtime.Serialization>.  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>Pour ajouter des données dans le Presse-papiers dans un format commun unique  
  
1. Utilisez le <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, ou <xref:System.Windows.Forms.Clipboard.SetText%2A> (méthode). Ces méthodes sont disponibles uniquement dans le .NET Framework 2.0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>Pour ajouter des données dans le Presse-papiers dans un format personnalisé  
  
1. Utilisez le <xref:System.Windows.Forms.Clipboard.SetData%2A> méthode avec un nom de format personnalisé. Cette méthode est uniquement disponible dans .NET Framework 2.0.  
  
     Vous pouvez également utiliser des noms de formats prédéfinis avec la <xref:System.Windows.Forms.Clipboard.SetData%2A> (méthode). Pour plus d'informations, consultez <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>Pour ajouter des données dans le Presse-papiers dans plusieurs formats  
  
1. Utilisez le <xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType> (méthode) et passez un <xref:System.Windows.Forms.DataObject> qui contient vos données. Vous devez utiliser cette méthode pour ajouter des données dans le Presse-papiers sur les versions antérieures à .NET Framework 2.0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérations glisser-déposer et prise en charge du Presse-papiers](drag-and-drop-operations-and-clipboard-support.md)
- [Guide pratique pour Récupérer des données à partir du Presse-papiers](how-to-retrieve-data-from-the-clipboard.md)
