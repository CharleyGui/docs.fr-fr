---
title: "Comment : lire des métadonnées d'image"
desription: Learn how to read the Windows Forms PropertyItems property of an Image object to retrieve all the metadata from a file.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 814cb17feba1e1e3a42b2bc403b0b4c828caf90e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174664"
---
# <a name="how-to-read-image-metadata"></a>Comment : lire des métadonnées d'image

Certains fichiers image contiennent des métadonnées que vous pouvez lire pour déterminer les fonctionnalités de l’image. Par exemple, une photographie numérique peut contenir des métadonnées que vous pouvez lire pour déterminer la marque et le modèle de l’appareil photo utilisé pour capturer l’image. Avec GDI+, vous pouvez lire les métadonnées existantes, et vous pouvez également écrire de nouvelles métadonnées dans des fichiers image.

GDI+ stocke un élément de métadonnées individuel dans un <xref:System.Drawing.Imaging.PropertyItem> objet. Vous pouvez lire la <xref:System.Drawing.Image.PropertyItems%2A> propriété d’un <xref:System.Drawing.Image> objet pour récupérer toutes les métadonnées d’un fichier. La <xref:System.Drawing.Image.PropertyItems%2A> propriété retourne un tableau d' <xref:System.Drawing.Imaging.PropertyItem> objets.

Un <xref:System.Drawing.Imaging.PropertyItem> objet a les quatre propriétés suivantes : `Id` , `Value` , `Len` et `Type` .

## <a name="id"></a>Id

Balise qui identifie l’élément de métadonnées. Certaines valeurs qui peuvent être assignées à <xref:System.Drawing.Imaging.PropertyItem.Id%2A> sont indiquées dans le tableau suivant :

|Valeur hexadécimale|Description|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Titre de l’image<br /><br /> Fabricant de l’équipement<br /><br /> Modèle d’équipement<br /><br /> ExifDTOriginal<br /><br /> Temps d’exposition EXIF<br /><br /> Table de luminance<br /><br /> Table de chrominance|

## <a name="value"></a>Valeur

Tableau de valeurs . Le format des valeurs est déterminé par la <xref:System.Drawing.Imaging.PropertyItem.Type%2A> propriété.

## <a name="len"></a>NbCar

Longueur (en octets) du tableau de valeurs vers lequel la <xref:System.Drawing.Imaging.PropertyItem.Value%2A> propriété pointe.

## <a name="type"></a>Type

Type de données des valeurs dans le tableau pointé par la `Value` propriété. Les formats indiqués par les `Type` valeurs de propriété sont indiqués dans le tableau suivant :

|Valeur numérique|Description|
|-------------------|-----------------|
|1|Un `Byte`|
|2|Tableau d' `Byte` objets encodés au format ASCII|
|3|Entier 16 bits|
|4|Entier 32 bits|
|5|Tableau de deux `Byte` objets qui représentent un nombre rationnel|
|6|Non utilisé|
|7|Indéfini|
|8|Non utilisé|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>Exemple
  
L’exemple de code suivant lit et affiche les sept éléments de métadonnées dans le fichier `FakePhoto.jpg` . Le deuxième élément de la propriété (index 1) de la liste a <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (fabricant de l’équipement) et <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (tableau d’octets encodé en ASCII). L’exemple de code affiche la valeur de cet élément de propriété.

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

Le code produit une sortie similaire à ce qui suit :

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

## <a name="compiling-the-code"></a>Compilation du code

L’exemple précédent est conçu pour être utilisé avec Windows Forms, et il nécessite <xref:System.Windows.Forms.PaintEventArgs> `e` , qui est un paramètre du <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements. Gérez l’événement du formulaire <xref:System.Windows.Forms.Control.Paint> et collez ce code dans le gestionnaire d’événements Paint. Vous devez remplacer `FakePhoto.jpg` par un nom d’image et un chemin d’accès valides sur votre système et importer l' `System.Drawing.Imaging` espace de noms.

## <a name="see-also"></a>Voir aussi

- [Images, bitmaps et métafichiers](images-bitmaps-and-metafiles.md)
- [Utilisation des images, bitmaps, icônes et métafichiers](working-with-images-bitmaps-icons-and-metafiles.md)
