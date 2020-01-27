---
title: Vue d'ensemble du composant PrintDocument
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a82cc0cdcb8cfae796c9c6bf60ab73873f85a291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728542"
---
# <a name="printdocument-component-overview-windows-forms"></a>Vue d'ensemble du composant PrintDocument (Windows Forms)

Le composant [PrintDocument](printdocument-component-windows-forms.md) Windows Forms permet de définir les propriétés qui décrivent les éléments à imprimer, puis d’imprimer le document dans des applications Windows. Il peut être utilisé conjointement avec le composant [PrintDialog](printdialog-component-windows-forms.md) pour contrôler tous les aspects de l’impression du document.

## <a name="working-with-the-printdocument-component"></a>Utilisation du composant PrintDocument

Deux des principaux scénarios qui impliquent le composant <xref:System.Drawing.Printing.PrintDocument> sont les suivants :

- Travaux d’impression simples, tels que l’impression d’un fichier texte. Dans ce cas, vous devez ajouter le composant <xref:System.Drawing.Printing.PrintDocument> à un Windows Form, puis ajouter une logique de programmation qui imprime un fichier dans le gestionnaire d’événements <xref:System.Drawing.Printing.PrintDocument.PrintPage>. La logique de programmation doit se déboucher sur la méthode <xref:System.Drawing.Printing.PrintDocument.Print%2A> pour imprimer le document. Cette méthode envoie un objet <xref:System.Drawing.Graphics>, contenu dans la propriété <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> de la classe <xref:System.Drawing.Printing.PrintPageEventArgs>, à l’imprimante. Pour obtenir un exemple qui montre comment imprimer un document texte à l’aide du composant <xref:System.Drawing.Printing.PrintDocument>, consultez [Comment : imprimer un fichier texte à plusieurs pages dans Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).

- Travaux d’impression plus complexes, comme lorsque vous souhaitez réutiliser la logique d’impression que vous avez écrite. Dans ce cas, vous devez dériver un nouveau composant du composant <xref:System.Drawing.Printing.PrintDocument> et remplacer (consultez [substitutions](../../../visual-basic/language-reference/modifiers/overrides.md) pour Visual Basic ou [remplacer](../../../csharp/language-reference/keywords/override.md) pour C#) l’événement <xref:System.Drawing.Printing.PrintDocument.PrintPage>.

Lorsqu’il est ajouté à un formulaire, le composant <xref:System.Drawing.Printing.PrintDocument> s’affiche dans la barre d’État en bas de la Concepteur Windows Forms dans Visual Studio.

## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [Prise en charge de l’impression dans les Windows Forms](../advanced/windows-forms-print-support.md)
- [Composant PrintDocument](printdocument-component-windows-forms.md)
