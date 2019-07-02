---
title: Métafichiers dans GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: df54289722cf12bad840722c6eafdaa43279a5dc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504587"
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="5e02a-102">Métafichiers dans GDI+</span><span class="sxs-lookup"><span data-stu-id="5e02a-102">Metafiles in GDI+</span></span>
<span data-ttu-id="5e02a-103">GDI + offre la <xref:System.Drawing.Imaging.Metafile> classe afin que vous pouvez enregistrer et afficher des métafichiers.</span><span class="sxs-lookup"><span data-stu-id="5e02a-103">GDI+ provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="5e02a-104">Un métafichier, également appelé image vectorielle, est une image qui est stockée comme une séquence de commandes et les paramètres de dessin.</span><span class="sxs-lookup"><span data-stu-id="5e02a-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="5e02a-105">Les commandes et les paramètres enregistrement dans un <xref:System.Drawing.Imaging.Metafile> objet peut être stocké en mémoire ou enregistré dans un fichier ou le flux.</span><span class="sxs-lookup"><span data-stu-id="5e02a-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="5e02a-106">Formats de métafichier</span><span class="sxs-lookup"><span data-stu-id="5e02a-106">Metafile Formats</span></span>  
 <span data-ttu-id="5e02a-107">GDI + peut afficher des métafichiers qui ont été stockés dans les formats suivants :</span><span class="sxs-lookup"><span data-stu-id="5e02a-107">GDI+ can display metafiles that have been stored in the following formats:</span></span>  
  
- <span data-ttu-id="5e02a-108">Métafichier Windows (WMF)</span><span class="sxs-lookup"><span data-stu-id="5e02a-108">Windows Metafile (WMF)</span></span>  
  
- <span data-ttu-id="5e02a-109">métafichier amélioré (EMF)</span><span class="sxs-lookup"><span data-stu-id="5e02a-109">Enhanced Metafile (EMF)</span></span>  
  
- <span data-ttu-id="5e02a-110">EMF+</span><span class="sxs-lookup"><span data-stu-id="5e02a-110">EMF+</span></span>  
  
 <span data-ttu-id="5e02a-111">GDI + peut enregistrer des métafichiers aux formats EMF et EMF +, mais pas dans le format WMF.</span><span class="sxs-lookup"><span data-stu-id="5e02a-111">GDI+ can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="5e02a-112">EMF + est une extension d’EMF qui permet de stocker des enregistrements GDI +.</span><span class="sxs-lookup"><span data-stu-id="5e02a-112">EMF+ is an extension to EMF that allows GDI+ records to be stored.</span></span> <span data-ttu-id="5e02a-113">Il existe deux variantes du format EMF + : EMF + uniquement et double EMF +.</span><span class="sxs-lookup"><span data-stu-id="5e02a-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="5e02a-114">Les métafichiers EMF + Only contiennent uniquement des enregistrements GDI +.</span><span class="sxs-lookup"><span data-stu-id="5e02a-114">EMF+ Only metafiles contain only GDI+ records.</span></span> <span data-ttu-id="5e02a-115">Ces métafichiers peuvent être affichés par GDI + mais pas par GDI.</span><span class="sxs-lookup"><span data-stu-id="5e02a-115">Such metafiles can be displayed by GDI+ but not by GDI.</span></span> <span data-ttu-id="5e02a-116">Les métafichiers EMF + Dual contiennent des enregistrements GDI + et GDI.</span><span class="sxs-lookup"><span data-stu-id="5e02a-116">EMF+ Dual metafiles contain GDI+ and GDI records.</span></span> <span data-ttu-id="5e02a-117">Chaque enregistrement GDI + d’un métafichier EMF + Dual est associé à un autre enregistrement GDI.</span><span class="sxs-lookup"><span data-stu-id="5e02a-117">Each GDI+ record in an EMF+ Dual metafile is paired with an alternate GDI record.</span></span> <span data-ttu-id="5e02a-118">Ces métafichiers peuvent être affichés par GDI + ou par GDI.</span><span class="sxs-lookup"><span data-stu-id="5e02a-118">Such metafiles can be displayed by GDI+ or by GDI.</span></span>  
  
 <span data-ttu-id="5e02a-119">L’exemple suivant affiche un métafichier précédemment enregistré en tant que fichier.</span><span class="sxs-lookup"><span data-stu-id="5e02a-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="5e02a-120">Le métafichier est affiché avec son coin supérieur gauche à (100, 100).</span><span class="sxs-lookup"><span data-stu-id="5e02a-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="5e02a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e02a-121">See also</span></span>

- [<span data-ttu-id="5e02a-122">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="5e02a-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
