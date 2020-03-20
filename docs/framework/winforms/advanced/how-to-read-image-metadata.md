---
title: "Comment : lire des métadonnées d'image"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: e2b56175e625281a920c390e5feb4238e3cb7f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182523"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="13f19-102">Comment : lire des métadonnées d'image</span><span class="sxs-lookup"><span data-stu-id="13f19-102">How to: Read Image Metadata</span></span>

<span data-ttu-id="13f19-103">Certains fichiers d’images contiennent des métadonnées que vous pouvez lire pour déterminer les caractéristiques de l’image.</span><span class="sxs-lookup"><span data-stu-id="13f19-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="13f19-104">Par exemple, une photographie numérique peut contenir des métadonnées que vous pouvez lire pour déterminer la marque et le modèle de la caméra utilisée pour capturer l’image.</span><span class="sxs-lookup"><span data-stu-id="13f19-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="13f19-105">Avec GDIMD, vous pouvez lire les métadonnées existantes, et vous pouvez également écrire de nouvelles métadonnées sur des fichiers d’images.</span><span class="sxs-lookup"><span data-stu-id="13f19-105">With GDI+, you can read existing metadata, and you can also write new metadata to image files.</span></span>

<span data-ttu-id="13f19-106">GDIMD stocke un morceau individuel <xref:System.Drawing.Imaging.PropertyItem> de métadonnées dans un objet.</span><span class="sxs-lookup"><span data-stu-id="13f19-106">GDI+ stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="13f19-107">Vous pouvez <xref:System.Drawing.Image.PropertyItems%2A> lire la <xref:System.Drawing.Image> propriété d’un objet pour récupérer toutes les métadonnées d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="13f19-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="13f19-108">La <xref:System.Drawing.Image.PropertyItems%2A> propriété retourne <xref:System.Drawing.Imaging.PropertyItem> une gamme d’objets.</span><span class="sxs-lookup"><span data-stu-id="13f19-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>

<span data-ttu-id="13f19-109">Un <xref:System.Drawing.Imaging.PropertyItem> objet a les `Id`quatre `Value` `Len`propriétés `Type`suivantes: , , , et .</span><span class="sxs-lookup"><span data-stu-id="13f19-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>

## <a name="id"></a><span data-ttu-id="13f19-110">Id</span><span class="sxs-lookup"><span data-stu-id="13f19-110">Id</span></span>

<span data-ttu-id="13f19-111">Une balise qui identifie l’élément métadonnée.</span><span class="sxs-lookup"><span data-stu-id="13f19-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="13f19-112">Certaines valeurs auxquelles on <xref:System.Drawing.Imaging.PropertyItem.Id%2A> peut attribuer sont indiquées dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="13f19-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table:</span></span>

|<span data-ttu-id="13f19-113">Valeur hexadécimale</span><span class="sxs-lookup"><span data-stu-id="13f19-113">Hexadecimal value</span></span>|<span data-ttu-id="13f19-114">Description</span><span class="sxs-lookup"><span data-stu-id="13f19-114">Description</span></span>|
|-----------------------|-----------------|
|<span data-ttu-id="13f19-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="13f19-115">0x0320</span></span><br /><br /> <span data-ttu-id="13f19-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="13f19-116">0x010F</span></span><br /><br /> <span data-ttu-id="13f19-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="13f19-117">0x0110</span></span><br /><br /> <span data-ttu-id="13f19-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="13f19-118">0x9003</span></span><br /><br /> <span data-ttu-id="13f19-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="13f19-119">0x829A</span></span><br /><br /> <span data-ttu-id="13f19-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="13f19-120">0x5090</span></span><br /><br /> <span data-ttu-id="13f19-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="13f19-121">0x5091</span></span>|<span data-ttu-id="13f19-122">Titre de l’image</span><span class="sxs-lookup"><span data-stu-id="13f19-122">Image title</span></span><br /><br /> <span data-ttu-id="13f19-123">Fabricant d’équipement</span><span class="sxs-lookup"><span data-stu-id="13f19-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="13f19-124">Modèle d’équipement</span><span class="sxs-lookup"><span data-stu-id="13f19-124">Equipment model</span></span><br /><br /> <span data-ttu-id="13f19-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="13f19-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="13f19-126">Temps d’exposition Exif</span><span class="sxs-lookup"><span data-stu-id="13f19-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="13f19-127">Table Luminance</span><span class="sxs-lookup"><span data-stu-id="13f19-127">Luminance table</span></span><br /><br /> <span data-ttu-id="13f19-128">Table de chrominance</span><span class="sxs-lookup"><span data-stu-id="13f19-128">Chrominance table</span></span>|

## <a name="value"></a><span data-ttu-id="13f19-129">Valeur</span><span class="sxs-lookup"><span data-stu-id="13f19-129">Value</span></span>

<span data-ttu-id="13f19-130">Tableau de valeurs .</span><span class="sxs-lookup"><span data-stu-id="13f19-130">An array of values.</span></span> <span data-ttu-id="13f19-131">Le format des valeurs est <xref:System.Drawing.Imaging.PropertyItem.Type%2A> déterminé par la propriété.</span><span class="sxs-lookup"><span data-stu-id="13f19-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>

## <a name="len"></a><span data-ttu-id="13f19-132">NbCar</span><span class="sxs-lookup"><span data-stu-id="13f19-132">Len</span></span>

<span data-ttu-id="13f19-133">La longueur (dans les octets) de l’éventail de valeurs indiquées par la <xref:System.Drawing.Imaging.PropertyItem.Value%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="13f19-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>

## <a name="type"></a><span data-ttu-id="13f19-134">Type</span><span class="sxs-lookup"><span data-stu-id="13f19-134">Type</span></span>

<span data-ttu-id="13f19-135">Le type de données des valeurs dans `Value` le tableau indiqué par la propriété.</span><span class="sxs-lookup"><span data-stu-id="13f19-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="13f19-136">Les formats indiqués par la valeur de la `Type` propriété sont indiqués dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="13f19-136">The formats indicated by the `Type` property values are shown in the following table:</span></span>

|<span data-ttu-id="13f19-137">Valeur numérique</span><span class="sxs-lookup"><span data-stu-id="13f19-137">Numeric value</span></span>|<span data-ttu-id="13f19-138">Description</span><span class="sxs-lookup"><span data-stu-id="13f19-138">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="13f19-139">1</span><span class="sxs-lookup"><span data-stu-id="13f19-139">1</span></span>|<span data-ttu-id="13f19-140">Une variable de type `Byte`.</span><span class="sxs-lookup"><span data-stu-id="13f19-140">A `Byte`</span></span>|
|<span data-ttu-id="13f19-141">2</span><span class="sxs-lookup"><span data-stu-id="13f19-141">2</span></span>|<span data-ttu-id="13f19-142">Une panoplie d’objets `Byte` codés sous forme d’ASCII</span><span class="sxs-lookup"><span data-stu-id="13f19-142">An array of `Byte` objects encoded as ASCII</span></span>|
|<span data-ttu-id="13f19-143">3</span><span class="sxs-lookup"><span data-stu-id="13f19-143">3</span></span>|<span data-ttu-id="13f19-144">Un intégrant 16 bits</span><span class="sxs-lookup"><span data-stu-id="13f19-144">A 16-bit integer</span></span>|
|<span data-ttu-id="13f19-145">4</span><span class="sxs-lookup"><span data-stu-id="13f19-145">4</span></span>|<span data-ttu-id="13f19-146">Un intégrant 32 bits</span><span class="sxs-lookup"><span data-stu-id="13f19-146">A 32-bit integer</span></span>|
|<span data-ttu-id="13f19-147">5</span><span class="sxs-lookup"><span data-stu-id="13f19-147">5</span></span>|<span data-ttu-id="13f19-148">Un tableau `Byte` de deux objets qui représentent un nombre rationnel</span><span class="sxs-lookup"><span data-stu-id="13f19-148">An array of two `Byte` objects that represent a rational number</span></span>|
|<span data-ttu-id="13f19-149">6</span><span class="sxs-lookup"><span data-stu-id="13f19-149">6</span></span>|<span data-ttu-id="13f19-150">Non utilisé</span><span class="sxs-lookup"><span data-stu-id="13f19-150">Not used</span></span>|
|<span data-ttu-id="13f19-151">7</span><span class="sxs-lookup"><span data-stu-id="13f19-151">7</span></span>|<span data-ttu-id="13f19-152">Indéfini</span><span class="sxs-lookup"><span data-stu-id="13f19-152">Undefined</span></span>|
|<span data-ttu-id="13f19-153">8</span><span class="sxs-lookup"><span data-stu-id="13f19-153">8</span></span>|<span data-ttu-id="13f19-154">Non utilisé</span><span class="sxs-lookup"><span data-stu-id="13f19-154">Not used</span></span>|
|<span data-ttu-id="13f19-155">9</span><span class="sxs-lookup"><span data-stu-id="13f19-155">9</span></span>|`SLong`|
|<span data-ttu-id="13f19-156">10</span><span class="sxs-lookup"><span data-stu-id="13f19-156">10</span></span>|`SRational`|

## <a name="example"></a><span data-ttu-id="13f19-157"> Exemple</span><span class="sxs-lookup"><span data-stu-id="13f19-157">Example</span></span>
  
<span data-ttu-id="13f19-158">L’exemple de code suivant lit et affiche les `FakePhoto.jpg`sept pièces de métadonnées dans le fichier .</span><span class="sxs-lookup"><span data-stu-id="13f19-158">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="13f19-159">Le deuxième élément de propriété (index <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 1) de la liste est <xref:System.Drawing.Imaging.PropertyItem.Type%2A> de 0x010F (fabricant d’équipement) et de 2 (tableau de byte codé par ASCII).</span><span class="sxs-lookup"><span data-stu-id="13f19-159">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="13f19-160">L’exemple de code affiche la valeur de cet article de propriété.</span><span class="sxs-lookup"><span data-stu-id="13f19-160">The code example displays the value of that property item.</span></span>

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

<span data-ttu-id="13f19-161">Le code produit des sorties similaires à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="13f19-161">The code produces output similar to the following:</span></span>

```output
 Property Item 0
  
 id: 0x320
  
 type: 2

 length: 16 bytes
  
 Property Item 1
  
 id: 0x10f
  
 type: 2
  
 length: 17 bytes
  
 Property Item 2
  
 id: 0x110
  
 type: 2
  
 length: 7 bytes
  
 Property Item 3
  
 id: 0x9003
  
 type: 2
  
 length: 20 bytes
  
 Property Item 4
  
 id: 0x829a
  
 type: 5
  
 length: 8 bytes
  
 Property Item 5
  
 id: 0x5090
  
 type: 3
  
 length: 128 bytes
  
 Property Item 6
  
 id: 0x5091
  
 type: 3
  
 length: 128 bytes
  
 The equipment make is Northwind Camera.
 ```

## <a name="compiling-the-code"></a><span data-ttu-id="13f19-162">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="13f19-162">Compiling the Code</span></span>

<span data-ttu-id="13f19-163">L’exemple précédent est conçu pour une <xref:System.Windows.Forms.PaintEventArgs> `e`utilisation avec Windows Forms, et il nécessite , qui est un paramètre du gestionnaire d’événements. <xref:System.Windows.Forms.Control.Paint></span><span class="sxs-lookup"><span data-stu-id="13f19-163">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="13f19-164">Gérez l’événement du <xref:System.Windows.Forms.Control.Paint> formulaire et collez ce code dans le gestionnaire d’événements de peinture.</span><span class="sxs-lookup"><span data-stu-id="13f19-164">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="13f19-165">Vous devez `FakePhoto.jpg` remplacer par un nom d’image `System.Drawing.Imaging` et un chemin valides sur votre système et importer l’espace nom.</span><span class="sxs-lookup"><span data-stu-id="13f19-165">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="13f19-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13f19-166">See also</span></span>

- [<span data-ttu-id="13f19-167">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="13f19-167">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="13f19-168">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="13f19-168">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
