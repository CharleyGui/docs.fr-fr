---
title: TextFieldParser ne prend pas en charge les jetons de commentaires qui contiennent un espace blanc
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_WhitespaceInToken
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
ms.openlocfilehash: 825f999f8eab3563dd77039ef19ae5e329bb4240
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078500"
---
# <a name="textfieldparser-does-not-support-comment-tokens-that-contain-white-space"></a><span data-ttu-id="0f347-102">TextFieldParser ne prend pas en charge les jetons de commentaires qui contiennent un espace blanc</span><span class="sxs-lookup"><span data-stu-id="0f347-102">TextFieldParser does not support comment tokens that contain white space</span></span>

<span data-ttu-id="0f347-103">Un jeton de commentaire qui contient un espace blanc a été fourni.</span><span class="sxs-lookup"><span data-stu-id="0f347-103">A comment token that contains white space has been supplied.</span></span> <span data-ttu-id="0f347-104">`TextFieldParser` ne prend pas en charge les jetons de commentaires qui contiennent un espace blanc, sauf si ce dernier se trouve au début du jeton.</span><span class="sxs-lookup"><span data-stu-id="0f347-104">The `TextFieldParser` does not support comment tokens that contain white space unless the white space occurs at the beginning of the token.</span></span> <span data-ttu-id="0f347-105">Un espace blanc situé au début d’un jeton est ignoré.</span><span class="sxs-lookup"><span data-stu-id="0f347-105">White space occurring at the beginning of a token is ignored.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f347-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="0f347-106">To correct this error</span></span>  
  
- <span data-ttu-id="0f347-107">Fournissez un jeton de commentaire correct.</span><span class="sxs-lookup"><span data-stu-id="0f347-107">Supply a correct comment token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f347-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f347-108">See also</span></span>

- [<span data-ttu-id="0f347-109">TextFieldParser.CommentTokens, propriété</span><span class="sxs-lookup"><span data-stu-id="0f347-109">TextFieldParser.CommentTokens Property</span></span>](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A)
- [<span data-ttu-id="0f347-110">Analyse des fichiers texte avec l'objet TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="0f347-110">Parsing Text Files with the TextFieldParser Object</span></span>](../developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="0f347-111">TextFieldParser Object</span><span class="sxs-lookup"><span data-stu-id="0f347-111">TextFieldParser Object</span></span>](../language-reference/objects/textfieldparser-object.md)
