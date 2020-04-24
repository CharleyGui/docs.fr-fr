---
title: 'Résolution des problèmes : lecture et écriture dans des fichiers texte'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: dbc53ca3cc9ae9b2d14b925f891d0409b2b7debd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333800"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="9dea0-102">Dépannage : lecture et écriture dans des fichiers texte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9dea0-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>

<span data-ttu-id="9dea0-103">Cette rubrique aborde les problèmes courants rencontrés lors de l’utilisation de fichiers texte et propose une approche pour chacun d’entre eux.</span><span class="sxs-lookup"><span data-stu-id="9dea0-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="9dea0-104">Problèmes courants</span><span class="sxs-lookup"><span data-stu-id="9dea0-104">Common problems</span></span>  

 <span data-ttu-id="9dea0-105">Les problèmes les plus fréquemment rencontrés lors de l’utilisation de fichiers texte incluent les exceptions de sécurité, les encodages de fichiers ou les chemins non valides.</span><span class="sxs-lookup"><span data-stu-id="9dea0-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="9dea0-106">Exceptions de sécurité</span><span class="sxs-lookup"><span data-stu-id="9dea0-106">Security exceptions</span></span>  

 <span data-ttu-id="9dea0-107">Une <xref:System.Security.SecurityException> est levée quand une erreur de sécurité se produit.</span><span class="sxs-lookup"><span data-stu-id="9dea0-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="9dea0-108">Cela est souvent dû au fait que l’utilisateur n’a pas les autorisations nécessaires, ce qui peut être résolu par l’ajout d’autorisations ou l’utilisation des fichiers dans un stockage isolé.</span><span class="sxs-lookup"><span data-stu-id="9dea0-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="9dea0-109">Encodages de fichiers</span><span class="sxs-lookup"><span data-stu-id="9dea0-109">File encodings</span></span>  

 <span data-ttu-id="9dea0-110">Les encodages de fichiers, également appelés codages de caractères, spécifient comment représenter les caractères lors du traitement du texte.</span><span class="sxs-lookup"><span data-stu-id="9dea0-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="9dea0-111">Les caractères inattendus d’un fichier texte peuvent résulter d’un encodage incorrect.</span><span class="sxs-lookup"><span data-stu-id="9dea0-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="9dea0-112">Pour la plupart des fichiers, un encodage peut être préférable à un autre en fonction des caractères de langue qu’il peut ou non gérer, bien qu’Unicode soit généralement préféré.</span><span class="sxs-lookup"><span data-stu-id="9dea0-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="9dea0-113">Pour plus d’informations, consultez [Encodages de fichiers](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) et <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="9dea0-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="9dea0-114">Chemins incorrects</span><span class="sxs-lookup"><span data-stu-id="9dea0-114">Incorrect paths</span></span>  

 <span data-ttu-id="9dea0-115">Lors de l’analyse des chemins, notamment des chemins relatifs, il est facile de fournir des données incorrectes.</span><span class="sxs-lookup"><span data-stu-id="9dea0-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="9dea0-116">Vous pouvez résoudre de nombreux problèmes en vous assurant de fournir le chemin correct.</span><span class="sxs-lookup"><span data-stu-id="9dea0-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="9dea0-117">Pour plus d’informations, consultez [Guide pratique pour analyser les chemins](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="9dea0-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dea0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9dea0-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="9dea0-119">Lecture à partir de fichiers</span><span class="sxs-lookup"><span data-stu-id="9dea0-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="9dea0-120">Écrire dans des fichiers</span><span class="sxs-lookup"><span data-stu-id="9dea0-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="9dea0-121">Analyse des fichiers texte avec l'objet TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="9dea0-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
