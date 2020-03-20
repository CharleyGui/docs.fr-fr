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
# <a name="how-to-read-image-metadata"></a>Comment : lire des métadonnées d'image

Certains fichiers d’images contiennent des métadonnées que vous pouvez lire pour déterminer les caractéristiques de l’image. Par exemple, une photographie numérique peut contenir des métadonnées que vous pouvez lire pour déterminer la marque et le modèle de la caméra utilisée pour capturer l’image. Avec GDIMD, vous pouvez lire les métadonnées existantes, et vous pouvez également écrire de nouvelles métadonnées sur des fichiers d’images.

GDIMD stocke un morceau individuel <xref:System.Drawing.Imaging.PropertyItem> de métadonnées dans un objet. Vous pouvez <xref:System.Drawing.Image.PropertyItems%2A> lire la <xref:System.Drawing.Image> propriété d’un objet pour récupérer toutes les métadonnées d’un fichier. La <xref:System.Drawing.Image.PropertyItems%2A> propriété retourne <xref:System.Drawing.Imaging.PropertyItem> une gamme d’objets.

Un <xref:System.Drawing.Imaging.PropertyItem> objet a les `Id`quatre `Value` `Len`propriétés `Type`suivantes: , , , et .

## <a name="id"></a>Id

Une balise qui identifie l’élément métadonnée. Certaines valeurs auxquelles on <xref:System.Drawing.Imaging.PropertyItem.Id%2A> peut attribuer sont indiquées dans le tableau suivant :

|Valeur hexadécimale|Description|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Titre de l’image<br /><br /> Fabricant d’équipement<br /><br /> Modèle d’équipement<br /><br /> ExifDTOriginal<br /><br /> Temps d’exposition Exif<br /><br /> Table Luminance<br /><br /> Table de chrominance|

## <a name="value"></a>Valeur

Tableau de valeurs . Le format des valeurs est <xref:System.Drawing.Imaging.PropertyItem.Type%2A> déterminé par la propriété.

## <a name="len"></a>NbCar

La longueur (dans les octets) de l’éventail de valeurs indiquées par la <xref:System.Drawing.Imaging.PropertyItem.Value%2A> propriété.

## <a name="type"></a>Type

Le type de données des valeurs dans `Value` le tableau indiqué par la propriété. Les formats indiqués par la valeur de la `Type` propriété sont indiqués dans le tableau suivant :

|Valeur numérique|Description|
|-------------------|-----------------|
|1|Une variable de type `Byte`.|
|2|Une panoplie d’objets `Byte` codés sous forme d’ASCII|
|3|Un intégrant 16 bits|
|4|Un intégrant 32 bits|
|5|Un tableau `Byte` de deux objets qui représentent un nombre rationnel|
|6|Non utilisé|
|7|Indéfini|
|8|Non utilisé|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a> Exemple
  
L’exemple de code suivant lit et affiche les `FakePhoto.jpg`sept pièces de métadonnées dans le fichier . Le deuxième élément de propriété (index <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 1) de la liste est <xref:System.Drawing.Imaging.PropertyItem.Type%2A> de 0x010F (fabricant d’équipement) et de 2 (tableau de byte codé par ASCII). L’exemple de code affiche la valeur de cet article de propriété.

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

Le code produit des sorties similaires à ce qui suit :

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

L’exemple précédent est conçu pour une <xref:System.Windows.Forms.PaintEventArgs> `e`utilisation avec Windows Forms, et il nécessite , qui est un paramètre du gestionnaire d’événements. <xref:System.Windows.Forms.Control.Paint> Gérez l’événement du <xref:System.Windows.Forms.Control.Paint> formulaire et collez ce code dans le gestionnaire d’événements de peinture. Vous devez `FakePhoto.jpg` remplacer par un nom d’image `System.Drawing.Imaging` et un chemin valides sur votre système et importer l’espace nom.

## <a name="see-also"></a>Voir aussi

- [Images, bitmaps et métafichiers](images-bitmaps-and-metafiles.md)
- [Utilisation des images, bitmaps, icônes et métafichiers](working-with-images-bitmaps-icons-and-metafiles.md)
