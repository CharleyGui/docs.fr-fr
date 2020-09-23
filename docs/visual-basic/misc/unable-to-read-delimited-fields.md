---
title: Impossible de lire les champs délimités, car un guillemet double ne constitue pas un délimiteur conforme lorsque EscapeQuotes a la valeur True
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: 29682edb78b848897ac2999f2d84dc1a9c1a3367
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100354"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a><span data-ttu-id="e3ae9-102">Impossible de lire les champs délimités, car un guillemet double ne constitue pas un délimiteur conforme lorsque EscapeQuotes a la valeur True</span><span class="sxs-lookup"><span data-stu-id="e3ae9-102">Unable to read delimited fields because a double quote is not a legal delimiter when EscapeQuotes is set to True</span></span>

<span data-ttu-id="e3ae9-103">Le `TextFieldParser` ne peut pas lire le fichier, car un guillemet (") a été fourni comme délimiteur et `EscapeQuotes` a la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="e3ae9-103">The `TextFieldParser` cannot read from the file because a quotation mark (") has been supplied as the delimiter and `EscapeQuotes` is set to `True`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e3ae9-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e3ae9-104">To correct this error</span></span>  
  
- <span data-ttu-id="e3ae9-105">Affectez la valeur `EscapeQuotes` à `False`.</span><span class="sxs-lookup"><span data-stu-id="e3ae9-105">Set `EscapeQuotes` to `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3ae9-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3ae9-106">See also</span></span>

- [<span data-ttu-id="e3ae9-107">TextFieldParser.SetDelimiters, méthode</span><span class="sxs-lookup"><span data-stu-id="e3ae9-107">TextFieldParser.SetDelimiters Method</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [<span data-ttu-id="e3ae9-108">Propriété TextFieldParser.Delimiters</span><span class="sxs-lookup"><span data-stu-id="e3ae9-108">TextFieldParser.Delimiters Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [<span data-ttu-id="e3ae9-109">Procédure : lire des fichiers texte délimités par des virgules</span><span class="sxs-lookup"><span data-stu-id="e3ae9-109">How to: Read From Comma-Delimited Text Files</span></span>](../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="e3ae9-110">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="e3ae9-110">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
