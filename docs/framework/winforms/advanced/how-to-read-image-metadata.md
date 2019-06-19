---
title: 'Procédure : lire des métadonnées d’image'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 3266724503960b8b45cd134dfa5b007a58d578fa
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169813"
---
# <a name="how-to-read-image-metadata"></a><span data-ttu-id="4574e-102">Procédure : lire des métadonnées d’image</span><span class="sxs-lookup"><span data-stu-id="4574e-102">How to: Read Image Metadata</span></span>
<span data-ttu-id="4574e-103">Certains fichiers image contiennent des métadonnées que vous pouvez lire pour déterminer les fonctionnalités de l’image.</span><span class="sxs-lookup"><span data-stu-id="4574e-103">Some image files contain metadata that you can read to determine features of the image.</span></span> <span data-ttu-id="4574e-104">Par exemple, une photographie numérique peut contenir des métadonnées que vous pouvez lire pour déterminer la marque et le modèle de l’appareil photo utilisé pour capturer l’image.</span><span class="sxs-lookup"><span data-stu-id="4574e-104">For example, a digital photograph might contain metadata that you can read to determine the make and model of the camera used to capture the image.</span></span> <span data-ttu-id="4574e-105">Avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez lire les métadonnées existantes et vous pouvez également écrire de nouvelles métadonnées dans des fichiers image.</span><span class="sxs-lookup"><span data-stu-id="4574e-105">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can read existing metadata, and you can also write new metadata to image files.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="4574e-106">stocke un élément individuel de métadonnées dans un <xref:System.Drawing.Imaging.PropertyItem> objet.</span><span class="sxs-lookup"><span data-stu-id="4574e-106">stores an individual piece of metadata in a <xref:System.Drawing.Imaging.PropertyItem> object.</span></span> <span data-ttu-id="4574e-107">Vous pouvez lire le <xref:System.Drawing.Image.PropertyItems%2A> propriété d’un <xref:System.Drawing.Image> objet pour récupérer toutes les métadonnées d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="4574e-107">You can read the <xref:System.Drawing.Image.PropertyItems%2A> property of an <xref:System.Drawing.Image> object to retrieve all the metadata from a file.</span></span> <span data-ttu-id="4574e-108">Le <xref:System.Drawing.Image.PropertyItems%2A> propriété renvoie un tableau de <xref:System.Drawing.Imaging.PropertyItem> objets.</span><span class="sxs-lookup"><span data-stu-id="4574e-108">The <xref:System.Drawing.Image.PropertyItems%2A> property returns an array of <xref:System.Drawing.Imaging.PropertyItem> objects.</span></span>  
  
 <span data-ttu-id="4574e-109">Un <xref:System.Drawing.Imaging.PropertyItem> objet possède les quatre propriétés suivantes : `Id`, `Value`, `Len`, et `Type`.</span><span class="sxs-lookup"><span data-stu-id="4574e-109">A <xref:System.Drawing.Imaging.PropertyItem> object has the following four properties: `Id`, `Value`, `Len`, and `Type`.</span></span>  
  
## <a name="id"></a><span data-ttu-id="4574e-110">Id</span><span class="sxs-lookup"><span data-stu-id="4574e-110">Id</span></span>  
 <span data-ttu-id="4574e-111">Une balise qui identifie l’élément de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="4574e-111">A tag that identifies the metadata item.</span></span> <span data-ttu-id="4574e-112">Certaines valeurs qui peuvent être affectés à <xref:System.Drawing.Imaging.PropertyItem.Id%2A> sont affichés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="4574e-112">Some values that can be assigned to <xref:System.Drawing.Imaging.PropertyItem.Id%2A> are shown in the following table.</span></span>  
  
|<span data-ttu-id="4574e-113">Valeur hexadécimale</span><span class="sxs-lookup"><span data-stu-id="4574e-113">Hexadecimal value</span></span>|<span data-ttu-id="4574e-114">Description</span><span class="sxs-lookup"><span data-stu-id="4574e-114">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="4574e-115">0x0320</span><span class="sxs-lookup"><span data-stu-id="4574e-115">0x0320</span></span><br /><br /> <span data-ttu-id="4574e-116">0x010F</span><span class="sxs-lookup"><span data-stu-id="4574e-116">0x010F</span></span><br /><br /> <span data-ttu-id="4574e-117">0x0110</span><span class="sxs-lookup"><span data-stu-id="4574e-117">0x0110</span></span><br /><br /> <span data-ttu-id="4574e-118">0x9003</span><span class="sxs-lookup"><span data-stu-id="4574e-118">0x9003</span></span><br /><br /> <span data-ttu-id="4574e-119">0x829A</span><span class="sxs-lookup"><span data-stu-id="4574e-119">0x829A</span></span><br /><br /> <span data-ttu-id="4574e-120">0x5090</span><span class="sxs-lookup"><span data-stu-id="4574e-120">0x5090</span></span><br /><br /> <span data-ttu-id="4574e-121">0x5091</span><span class="sxs-lookup"><span data-stu-id="4574e-121">0x5091</span></span>|<span data-ttu-id="4574e-122">Titre de l’image</span><span class="sxs-lookup"><span data-stu-id="4574e-122">Image title</span></span><br /><br /> <span data-ttu-id="4574e-123">Fabricant OEM</span><span class="sxs-lookup"><span data-stu-id="4574e-123">Equipment manufacturer</span></span><br /><br /> <span data-ttu-id="4574e-124">Modèle de matériel</span><span class="sxs-lookup"><span data-stu-id="4574e-124">Equipment model</span></span><br /><br /> <span data-ttu-id="4574e-125">ExifDTOriginal</span><span class="sxs-lookup"><span data-stu-id="4574e-125">ExifDTOriginal</span></span><br /><br /> <span data-ttu-id="4574e-126">Temps d’exposition EXIF</span><span class="sxs-lookup"><span data-stu-id="4574e-126">Exif exposure time</span></span><br /><br /> <span data-ttu-id="4574e-127">Table de luminance</span><span class="sxs-lookup"><span data-stu-id="4574e-127">Luminance table</span></span><br /><br /> <span data-ttu-id="4574e-128">Table de chrominance</span><span class="sxs-lookup"><span data-stu-id="4574e-128">Chrominance table</span></span>|  
  
## <a name="value"></a><span data-ttu-id="4574e-129">Value</span><span class="sxs-lookup"><span data-stu-id="4574e-129">Value</span></span>  
 <span data-ttu-id="4574e-130">Un tableau de valeurs.</span><span class="sxs-lookup"><span data-stu-id="4574e-130">An array of values.</span></span> <span data-ttu-id="4574e-131">Le format des valeurs est déterminé par le <xref:System.Drawing.Imaging.PropertyItem.Type%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="4574e-131">The format of the values is determined by the <xref:System.Drawing.Imaging.PropertyItem.Type%2A> property.</span></span>  
  
## <a name="len"></a><span data-ttu-id="4574e-132">Len</span><span class="sxs-lookup"><span data-stu-id="4574e-132">Len</span></span>  
 <span data-ttu-id="4574e-133">La longueur (en octets) du tableau de valeurs vers lequel pointe le <xref:System.Drawing.Imaging.PropertyItem.Value%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="4574e-133">The length (in bytes) of the array of values pointed to by the <xref:System.Drawing.Imaging.PropertyItem.Value%2A> property.</span></span>  
  
## <a name="type"></a><span data-ttu-id="4574e-134">Type</span><span class="sxs-lookup"><span data-stu-id="4574e-134">Type</span></span>  
 <span data-ttu-id="4574e-135">Le type de données des valeurs dans le tableau vers lequel pointe le `Value` propriété.</span><span class="sxs-lookup"><span data-stu-id="4574e-135">The data type of the values in the array pointed to by the `Value` property.</span></span> <span data-ttu-id="4574e-136">Les formats indiqués par les `Type` les valeurs de propriété sont affichées dans le tableau suivant</span><span class="sxs-lookup"><span data-stu-id="4574e-136">The formats indicated by the `Type` property values are shown in the following table</span></span>  
  
|<span data-ttu-id="4574e-137">Valeur numérique</span><span class="sxs-lookup"><span data-stu-id="4574e-137">Numeric value</span></span>|<span data-ttu-id="4574e-138">Description</span><span class="sxs-lookup"><span data-stu-id="4574e-138">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="4574e-139">1</span><span class="sxs-lookup"><span data-stu-id="4574e-139">1</span></span>|<span data-ttu-id="4574e-140">`Byte`</span><span class="sxs-lookup"><span data-stu-id="4574e-140">A `Byte`</span></span>|  
|<span data-ttu-id="4574e-141">2</span><span class="sxs-lookup"><span data-stu-id="4574e-141">2</span></span>|<span data-ttu-id="4574e-142">Un tableau de `Byte` objets codés au format ASCII</span><span class="sxs-lookup"><span data-stu-id="4574e-142">An array of `Byte` objects encoded as ASCII</span></span>|  
|<span data-ttu-id="4574e-143">3</span><span class="sxs-lookup"><span data-stu-id="4574e-143">3</span></span>|<span data-ttu-id="4574e-144">Un entier 16 bits</span><span class="sxs-lookup"><span data-stu-id="4574e-144">A 16-bit integer</span></span>|  
|<span data-ttu-id="4574e-145">4</span><span class="sxs-lookup"><span data-stu-id="4574e-145">4</span></span>|<span data-ttu-id="4574e-146">Un entier 32 bits</span><span class="sxs-lookup"><span data-stu-id="4574e-146">A 32-bit integer</span></span>|  
|<span data-ttu-id="4574e-147">5</span><span class="sxs-lookup"><span data-stu-id="4574e-147">5</span></span>|<span data-ttu-id="4574e-148">Un tableau de deux `Byte` objets qui représentent un nombre rationnel</span><span class="sxs-lookup"><span data-stu-id="4574e-148">An array of two `Byte` objects that represent a rational number</span></span>|  
|<span data-ttu-id="4574e-149">6</span><span class="sxs-lookup"><span data-stu-id="4574e-149">6</span></span>|<span data-ttu-id="4574e-150">Non utilisé</span><span class="sxs-lookup"><span data-stu-id="4574e-150">Not used</span></span>|  
|<span data-ttu-id="4574e-151">7</span><span class="sxs-lookup"><span data-stu-id="4574e-151">7</span></span>|<span data-ttu-id="4574e-152">Undefined</span><span class="sxs-lookup"><span data-stu-id="4574e-152">Undefined</span></span>|  
|<span data-ttu-id="4574e-153">8</span><span class="sxs-lookup"><span data-stu-id="4574e-153">8</span></span>|<span data-ttu-id="4574e-154">Non utilisé</span><span class="sxs-lookup"><span data-stu-id="4574e-154">Not used</span></span>|  
|<span data-ttu-id="4574e-155">9</span><span class="sxs-lookup"><span data-stu-id="4574e-155">9</span></span>|`SLong`|  
|<span data-ttu-id="4574e-156">10</span><span class="sxs-lookup"><span data-stu-id="4574e-156">10</span></span>|`SRational`|  
  
## <a name="example"></a><span data-ttu-id="4574e-157">Exemple</span><span class="sxs-lookup"><span data-stu-id="4574e-157">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4574e-158">Description</span><span class="sxs-lookup"><span data-stu-id="4574e-158">Description</span></span>  
 <span data-ttu-id="4574e-159">L’exemple de code suivant lit et affiche les sept de métadonnées dans le fichier `FakePhoto.jpg`.</span><span class="sxs-lookup"><span data-stu-id="4574e-159">The following code example reads and displays the seven pieces of metadata in the file `FakePhoto.jpg`.</span></span> <span data-ttu-id="4574e-160">Le second élément de propriété (index 1) dans la liste a <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (fabricant) et <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (tableau d’octets encodé en ASCII).</span><span class="sxs-lookup"><span data-stu-id="4574e-160">The second (index 1) property item in the list has <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (equipment manufacturer) and <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ASCII-encoded byte array).</span></span> <span data-ttu-id="4574e-161">L’exemple de code affiche la valeur de cet élément de propriété.</span><span class="sxs-lookup"><span data-stu-id="4574e-161">The code example displays the value of that property item.</span></span>  
  
 <span data-ttu-id="4574e-162">Le code produit une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="4574e-162">The code produces output similar to the following:</span></span>  
 
```
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
  
### <a name="code"></a><span data-ttu-id="4574e-163">Code</span><span class="sxs-lookup"><span data-stu-id="4574e-163">Code</span></span>  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4574e-164">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="4574e-164">Compiling the Code</span></span>  
 <span data-ttu-id="4574e-165">L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="4574e-165">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="4574e-166">Gérer le formulaire <xref:System.Windows.Forms.Control.Paint> événements et collez ce code dans le Gestionnaire d’événements paint.</span><span class="sxs-lookup"><span data-stu-id="4574e-166">Handle the form's <xref:System.Windows.Forms.Control.Paint> event and paste this code into the paint event handler.</span></span> <span data-ttu-id="4574e-167">Vous devez remplacer `FakePhoto.jpg` avec un nom de l’image et le chemin d’accès valide sur votre système et à importer le `System.Drawing.Imaging` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4574e-167">You must replace `FakePhoto.jpg` with an image name and path valid on your system and import the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4574e-168">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4574e-168">See also</span></span>

- [<span data-ttu-id="4574e-169">Images, bitmaps et métafichiers</span><span class="sxs-lookup"><span data-stu-id="4574e-169">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="4574e-170">Utilisation des images, bitmaps, icônes et métafichiers</span><span class="sxs-lookup"><span data-stu-id="4574e-170">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
