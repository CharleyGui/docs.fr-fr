---
title: Encodages de fichiers (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: d73226c58d39c970ec02c32a2c188f2747a7d87e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583466"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="41f2a-102">Encodages de fichiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41f2a-102">File Encodings (Visual Basic)</span></span>

<span data-ttu-id="41f2a-103">Les encodages de fichiers, également appelés codages de caractères, spécifient comment représenter les caractères lors du traitement du texte.</span><span class="sxs-lookup"><span data-stu-id="41f2a-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="41f2a-104">Un encodage peut être préférable à un autre en fonction des caractères de langue qu’il peut ou non gérer, bien qu’Unicode soit généralement privilégié.</span><span class="sxs-lookup"><span data-stu-id="41f2a-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>

<span data-ttu-id="41f2a-105">Lors de la lecture ou de l’écriture dans des fichiers, des incohérences d’encodage de fichiers peuvent provoquer des exceptions ou des résultats incorrects.</span><span class="sxs-lookup"><span data-stu-id="41f2a-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>

## <a name="types-of-encodings"></a><span data-ttu-id="41f2a-106">Types d’encodages</span><span class="sxs-lookup"><span data-stu-id="41f2a-106">Types of Encodings</span></span>

<span data-ttu-id="41f2a-107">Unicode est l’encodage à utiliser par défaut quand vous travaillez avec des fichiers.</span><span class="sxs-lookup"><span data-stu-id="41f2a-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="41f2a-108">Unicode est une norme internationale d’encodage de caractères qui utilise des valeurs de code de 16 bits pour représenter tous les caractères utilisés dans l’informatique moderne, notamment les symboles techniques et les caractères spéciaux utilisés dans l’édition.</span><span class="sxs-lookup"><span data-stu-id="41f2a-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>

<span data-ttu-id="41f2a-109">Les anciennes normes d’encodage de caractères se composaient de jeux de caractères traditionnels, tels que le jeu de caractères ANSI Windows qui utilise des valeurs de code de 8 bits ou des combinaisons de valeurs de 8 bits, pour représenter les caractères utilisés dans une langue ou une région géographique spécifique.</span><span class="sxs-lookup"><span data-stu-id="41f2a-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>

## <a name="encoding-class"></a><span data-ttu-id="41f2a-110">Classe d’encodage</span><span class="sxs-lookup"><span data-stu-id="41f2a-110">Encoding Class</span></span>

<span data-ttu-id="41f2a-111">La classe <xref:System.Text.Encoding> représente un encodage de caractères.</span><span class="sxs-lookup"><span data-stu-id="41f2a-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="41f2a-112">Ce tableau liste et décrit les types d’encodages disponibles.</span><span class="sxs-lookup"><span data-stu-id="41f2a-112">This table lists the type of encodings available and describes each.</span></span>

|<span data-ttu-id="41f2a-113">Name</span><span class="sxs-lookup"><span data-stu-id="41f2a-113">Name</span></span>|<span data-ttu-id="41f2a-114">Description</span><span class="sxs-lookup"><span data-stu-id="41f2a-114">Description</span></span>|
|---|---|
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="41f2a-115">Représente un encodage de caractères ASCII de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="41f2a-115">Represents an ASCII character encoding of Unicode characters.</span></span>|
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="41f2a-116">Représente un encodage UTF-16 de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="41f2a-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="41f2a-117">Représente un encodage UTF-32 de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="41f2a-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="41f2a-118">Représente un encodage UTF-7 de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="41f2a-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="41f2a-119">Représente un encodage UTF-8 de caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="41f2a-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|

## <a name="see-also"></a><span data-ttu-id="41f2a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41f2a-120">See also</span></span>

- [<span data-ttu-id="41f2a-121">Lecture à partir de fichiers</span><span class="sxs-lookup"><span data-stu-id="41f2a-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="41f2a-122">Écriture dans des fichiers</span><span class="sxs-lookup"><span data-stu-id="41f2a-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
