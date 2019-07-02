---
title: Utilisation d'encodeurs et de décodeurs d'images dans GDI+ managé
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: 8cd66f3ce3da462867da9e23c38b3f6d877c058c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505093"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="c14fc-102">Utilisation d'encodeurs et de décodeurs d'images dans GDI+ managé</span><span class="sxs-lookup"><span data-stu-id="c14fc-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="c14fc-103">Le <xref:System.Drawing> espace de noms fournit le <xref:System.Drawing.Image> et <xref:System.Drawing.Bitmap> classes pour stocker et manipuler des images.</span><span class="sxs-lookup"><span data-stu-id="c14fc-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="c14fc-104">En utilisant des encodeurs d’images dans GDI +, vous pouvez écrire des images de la mémoire sur le disque.</span><span class="sxs-lookup"><span data-stu-id="c14fc-104">By using image encoders in GDI+, you can write images from memory to disk.</span></span> <span data-ttu-id="c14fc-105">À l’aide de décodeurs d’images dans GDI +, vous pouvez charger des images à partir du disque dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="c14fc-105">By using image decoders in GDI+, you can load images from disk into memory.</span></span> <span data-ttu-id="c14fc-106">Un encodeur traduit les données dans un <xref:System.Drawing.Image> ou <xref:System.Drawing.Bitmap> objet dans un format de fichier de disque désigné.</span><span class="sxs-lookup"><span data-stu-id="c14fc-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="c14fc-107">Un décodeur traduit les données dans un fichier de disque au format requis par le <xref:System.Drawing.Image> et <xref:System.Drawing.Bitmap> objets.</span><span class="sxs-lookup"><span data-stu-id="c14fc-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="c14fc-108">GDI + a intégré encodeurs et décodeurs qui prennent en charge les types de fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="c14fc-108">GDI+ has built-in encoders and decoders that support the following file types:</span></span>  
  
- <span data-ttu-id="c14fc-109">BMP</span><span class="sxs-lookup"><span data-stu-id="c14fc-109">BMP</span></span>  
  
- <span data-ttu-id="c14fc-110">GIF</span><span class="sxs-lookup"><span data-stu-id="c14fc-110">GIF</span></span>  
  
- <span data-ttu-id="c14fc-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="c14fc-111">JPEG</span></span>  
  
- <span data-ttu-id="c14fc-112">PNG</span><span class="sxs-lookup"><span data-stu-id="c14fc-112">PNG</span></span>  
  
- <span data-ttu-id="c14fc-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="c14fc-113">TIFF</span></span>  
  
 <span data-ttu-id="c14fc-114">GDI + possède également des décodeurs intégrés qui prennent en charge les types de fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="c14fc-114">GDI+ also has built-in decoders that support the following file types:</span></span>  
  
- <span data-ttu-id="c14fc-115">WMF</span><span class="sxs-lookup"><span data-stu-id="c14fc-115">WMF</span></span>  
  
- <span data-ttu-id="c14fc-116">EMF</span><span class="sxs-lookup"><span data-stu-id="c14fc-116">EMF</span></span>  
  
- <span data-ttu-id="c14fc-117">ICÔNE</span><span class="sxs-lookup"><span data-stu-id="c14fc-117">ICON</span></span>  
  
 <span data-ttu-id="c14fc-118">Les rubriques suivantes traitent des encodeurs et décodeurs plus en détail :</span><span class="sxs-lookup"><span data-stu-id="c14fc-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c14fc-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c14fc-119">In This Section</span></span>  
 [<span data-ttu-id="c14fc-120">Guide pratique pour Répertorier les encodeurs installés</span><span class="sxs-lookup"><span data-stu-id="c14fc-120">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)  
 <span data-ttu-id="c14fc-121">Décrit comment répertorier les encodeurs disponibles sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c14fc-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="c14fc-122">Guide pratique pour Répertorier les décodeurs installés</span><span class="sxs-lookup"><span data-stu-id="c14fc-122">How to: List Installed Decoders</span></span>](how-to-list-installed-decoders.md)  
 <span data-ttu-id="c14fc-123">Décrit comment répertorier les décodeurs disponibles sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c14fc-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="c14fc-124">Guide pratique pour Déterminer les paramètres pris en charge par un encodeur</span><span class="sxs-lookup"><span data-stu-id="c14fc-124">How to: Determine the Parameters Supported by an Encoder</span></span>](how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="c14fc-125">Décrit comment répertorier les <xref:System.Drawing.Imaging.EncoderParameters> pris en charge par un encodeur.</span><span class="sxs-lookup"><span data-stu-id="c14fc-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="c14fc-126">Guide pratique pour Convertir une image BMP en une image PNG</span><span class="sxs-lookup"><span data-stu-id="c14fc-126">How to: Convert a BMP image to a PNG image</span></span>](how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="c14fc-127">Décrit comment enregistrer une image dans un format d’image différent.</span><span class="sxs-lookup"><span data-stu-id="c14fc-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="c14fc-128">Guide pratique pour Définir au niveau de Compression JPEG</span><span class="sxs-lookup"><span data-stu-id="c14fc-128">How to: Set JPEG Compression Level</span></span>](how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="c14fc-129">Décrit comment modifier le niveau de qualité d’une image.</span><span class="sxs-lookup"><span data-stu-id="c14fc-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c14fc-130">Référence</span><span class="sxs-lookup"><span data-stu-id="c14fc-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="c14fc-131">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="c14fc-131">Related Sections</span></span>  
 [<span data-ttu-id="c14fc-132">À propos du code managé GDI+</span><span class="sxs-lookup"><span data-stu-id="c14fc-132">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
  
 [<span data-ttu-id="c14fc-133">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="c14fc-133">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
