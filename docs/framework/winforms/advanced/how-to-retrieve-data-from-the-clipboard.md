---
title: 'Procédure : récupérer des données dans le Presse-papiers'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: ca24615049abcc145698c033f31e6c98a38253bf
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040566"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Procédure : récupérer des données dans le Presse-papiers

La <xref:System.Windows.Forms.Clipboard> classe fournit des méthodes que vous pouvez utiliser pour interagir avec la fonctionnalité du presse-papiers du système d’exploitation Windows. De nombreuses applications utilisent le presse-papiers comme référentiel temporaire pour les données. Par exemple, les traitements de texte utilisent le presse-papiers pendant les opérations de couper-coller. Le presse-papiers est également utile pour transférer des informations d’une application à une autre.

Certaines applications stockent des données dans le presse-papiers dans plusieurs formats pour augmenter le nombre d’autres applications susceptibles d’utiliser les données. Un format de presse-papiers est une chaîne qui identifie le format. Une application qui utilise le format identifié peut récupérer les données associées dans le presse-papiers. La <xref:System.Windows.Forms.DataFormats> classe fournit des noms de format prédéfinis pour votre utilisation. Vous pouvez également utiliser vos propres noms de format ou utiliser le type d’un objet comme format. Pour plus d’informations sur l’ajout de données dans [le presse-papiers, consultez Procédure: Ajoutez des données au presse](how-to-add-data-to-the-clipboard.md)-papiers.

Pour déterminer si le presse-papiers contient des données dans un format particulier, utilisez `Contains`l’une des méthodes <xref:System.Windows.Forms.Clipboard.GetData%2A> de *format* ou la méthode. Pour récupérer des données du presse-papiers, utilisez l' `Get`une des méthodes de <xref:System.Windows.Forms.Clipboard.GetData%2A> *format* ou la méthode. Ces méthodes sont nouvelles dans .NET Framework 2,0.

Pour accéder aux données à partir du presse-papiers en utilisant des versions antérieures à <xref:System.Windows.Forms.Clipboard.GetDataObject%2A?displayProperty=nameWithType> .NET Framework 2,0, utilisez la méthode et appelez <xref:System.Windows.Forms.IDataObject>les méthodes du retourné. Pour déterminer si un format particulier est disponible dans l’objet retourné, par exemple, appelez la <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> méthode.

> [!NOTE]
> Toutes les applications Windows partagent le presse-papiers du système. Par conséquent, le contenu est susceptible d’être modifié lorsque vous basculez vers une autre application.
>
> La <xref:System.Windows.Forms.Clipboard> classe ne peut être utilisée que dans les threads définis en mode STA (single thread Apartment). Pour utiliser cette classe, assurez- `Main` vous que votre méthode est <xref:System.STAThreadAttribute> marquée avec l’attribut.

### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Pour récupérer des données du presse-papiers dans un format commun unique

1. Utilisez la <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>méthode <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A> ,<xref:System.Windows.Forms.Clipboard.GetImage%2A>, ou <xref:System.Windows.Forms.Clipboard.GetText%2A> . Si vous le souhaitez, utilisez `Contains`d’abord les méthodes de *format* correspondantes pour déterminer si les données sont disponibles dans un format particulier. Ces méthodes sont disponibles uniquement dans .NET Framework 2,0.

    [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
    [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]

### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Pour récupérer des données du presse-papiers dans un format personnalisé

1. Utilisez la <xref:System.Windows.Forms.Clipboard.GetData%2A> méthode avec un nom de format personnalisé. Cette méthode est disponible uniquement dans .NET Framework 2,0.

    Vous pouvez également utiliser des noms de format prédéfinis <xref:System.Windows.Forms.Clipboard.SetData%2A> avec la méthode. Pour plus d'informations, consultez <xref:System.Windows.Forms.DataFormats>.

    [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
    [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Pour récupérer des données du presse-papiers dans plusieurs formats

1. Utilisez la méthode <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>. Vous devez utiliser cette méthode pour récupérer des données du presse-papiers sur les versions antérieures à .NET Framework 2,0.

    [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
    [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

## <a name="see-also"></a>Voir aussi

- [Opérations glisser-déposer et prise en charge du Presse-papiers](drag-and-drop-operations-and-clipboard-support.md)
- [Guide pratique : Ajouter des données au Presse-papiers](how-to-add-data-to-the-clipboard.md)
