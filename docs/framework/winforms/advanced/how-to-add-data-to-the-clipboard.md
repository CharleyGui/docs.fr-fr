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
ms.openlocfilehash: d4afcd6ce942d1cd2286e3f393ce61436821bb3a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955127"
---
# <a name="how-to-add-data-to-the-clipboard"></a>Procédure : ajouter des données au Presse-papiers
La <xref:System.Windows.Forms.Clipboard> classe fournit des méthodes que vous pouvez utiliser pour interagir avec la fonctionnalité du presse-papiers du système d’exploitation Windows. De nombreuses applications utilisent le presse-papiers comme référentiel temporaire pour les données. Par exemple, les traitements de texte utilisent le presse-papiers pendant les opérations de couper-coller. Le presse-papiers est également utile pour transférer des données d’une application à une autre.  
  
 Lorsque vous ajoutez des données au Presse-papiers, vous pouvez indiquer le format de données afin que d’autres applications puissent reconnaître les données si elles peuvent utiliser ce format. Vous pouvez également ajouter des données au Presse-papiers dans plusieurs formats différents afin d’augmenter le nombre d’autres applications susceptibles d’utiliser les données.  
  
 Un format de presse-papiers est une chaîne qui identifie le format afin qu’une application qui utilise ce format puisse récupérer les données associées. La <xref:System.Windows.Forms.DataFormats> classe fournit des noms de format prédéfinis pour votre utilisation. Vous pouvez également utiliser vos propres noms de format ou utiliser le type d’un objet comme format.  
  
 Pour ajouter des données au Presse-papiers dans un ou plusieurs formats, <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> utilisez la méthode. Vous pouvez passer n’importe quel objet à cette méthode, mais pour ajouter des données dans plusieurs formats, vous devez d’abord ajouter les données à un objet distinct conçu pour utiliser plusieurs formats. En général, vous allez ajouter vos données à <xref:System.Windows.Forms.DataObject>un, mais vous pouvez utiliser n’importe quel type qui <xref:System.Windows.Forms.IDataObject> implémente l’interface.  
  
 Dans .NET Framework 2,0, vous pouvez ajouter des données directement au Presse-papiers en utilisant de nouvelles méthodes conçues pour faciliter les tâches de base du presse-papiers. Utilisez ces méthodes lorsque vous travaillez avec des données dans un format commun unique, tel que du texte.  
  
> [!NOTE]
> Toutes les applications Windows partagent le presse-papiers. Par conséquent, le contenu est susceptible d’être modifié lorsque vous basculez vers une autre application.  
>   
>  La <xref:System.Windows.Forms.Clipboard> classe ne peut être utilisée que dans les threads définis en mode STA (single thread Apartment). Pour utiliser cette classe, assurez- `Main` vous que votre méthode est <xref:System.STAThreadAttribute> marquée avec l’attribut.  
>   
>  Un objet doit être sérialisable pour être placé dans le presse-papiers. Pour rendre un type sérialisable, marquez-le avec <xref:System.SerializableAttribute> l’attribut. Si vous transmettez un objet non sérialisable à une méthode de presse-papiers, la méthode échoue sans lever d’exception. Pour plus d'informations sur la sérialisation, consultez <xref:System.Runtime.Serialization>.  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>Pour ajouter des données au Presse-papiers dans un format commun unique  
  
1. Utilisez la <xref:System.Windows.Forms.Clipboard.SetAudio%2A>méthode <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A> ,<xref:System.Windows.Forms.Clipboard.SetImage%2A>, ou <xref:System.Windows.Forms.Clipboard.SetText%2A> . Ces méthodes sont disponibles uniquement dans .NET Framework 2,0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>Pour ajouter des données au Presse-papiers dans un format personnalisé  
  
1. Utilisez la <xref:System.Windows.Forms.Clipboard.SetData%2A> méthode avec un nom de format personnalisé. Cette méthode est disponible uniquement dans .NET Framework 2,0.  
  
     Vous pouvez également utiliser des noms de format prédéfinis <xref:System.Windows.Forms.Clipboard.SetData%2A> avec la méthode. Pour plus d'informations, consultez <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>Pour ajouter des données au Presse-papiers dans plusieurs formats  
  
1. Utilisez la <xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType> méthode et transmettez une <xref:System.Windows.Forms.DataObject> qui contient vos données. Vous devez utiliser cette méthode pour ajouter des données au Presse-papiers sur les versions antérieures à .NET Framework 2,0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Voir aussi

- [Opérations glisser-déposer et prise en charge du Presse-papiers](drag-and-drop-operations-and-clipboard-support.md)
- [Guide pratique pour Récupérer les données du presse-papiers](how-to-retrieve-data-from-the-clipboard.md)
