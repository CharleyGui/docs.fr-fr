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
# <a name="how-to-read-image-metadata"></a>Procédure : lire des métadonnées d’image
Certains fichiers image contiennent des métadonnées que vous pouvez lire pour déterminer les fonctionnalités de l’image. Par exemple, une photographie numérique peut contenir des métadonnées que vous pouvez lire pour déterminer la marque et le modèle de l’appareil photo utilisé pour capturer l’image. Avec [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], vous pouvez lire les métadonnées existantes et vous pouvez également écrire de nouvelles métadonnées dans des fichiers image.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] stocke un élément individuel de métadonnées dans un <xref:System.Drawing.Imaging.PropertyItem> objet. Vous pouvez lire le <xref:System.Drawing.Image.PropertyItems%2A> propriété d’un <xref:System.Drawing.Image> objet pour récupérer toutes les métadonnées d’un fichier. Le <xref:System.Drawing.Image.PropertyItems%2A> propriété renvoie un tableau de <xref:System.Drawing.Imaging.PropertyItem> objets.  
  
 Un <xref:System.Drawing.Imaging.PropertyItem> objet possède les quatre propriétés suivantes : `Id`, `Value`, `Len`, et `Type`.  
  
## <a name="id"></a>Id  
 Une balise qui identifie l’élément de métadonnées. Certaines valeurs qui peuvent être affectés à <xref:System.Drawing.Imaging.PropertyItem.Id%2A> sont affichés dans le tableau suivant.  
  
|Valeur hexadécimale|Description|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Titre de l’image<br /><br /> Fabricant OEM<br /><br /> Modèle de matériel<br /><br /> ExifDTOriginal<br /><br /> Temps d’exposition EXIF<br /><br /> Table de luminance<br /><br /> Table de chrominance|  
  
## <a name="value"></a>Value  
 Un tableau de valeurs. Le format des valeurs est déterminé par le <xref:System.Drawing.Imaging.PropertyItem.Type%2A> propriété.  
  
## <a name="len"></a>Len  
 La longueur (en octets) du tableau de valeurs vers lequel pointe le <xref:System.Drawing.Imaging.PropertyItem.Value%2A> propriété.  
  
## <a name="type"></a>Type  
 Le type de données des valeurs dans le tableau vers lequel pointe le `Value` propriété. Les formats indiqués par les `Type` les valeurs de propriété sont affichées dans le tableau suivant  
  
|Valeur numérique|Description|  
|-------------------|-----------------|  
|1|`Byte`|  
|2|Un tableau de `Byte` objets codés au format ASCII|  
|3|Un entier 16 bits|  
|4|Un entier 32 bits|  
|5|Un tableau de deux `Byte` objets qui représentent un nombre rationnel|  
|6|Non utilisé|  
|7|Undefined|  
|8|Non utilisé|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple de code suivant lit et affiche les sept de métadonnées dans le fichier `FakePhoto.jpg`. Le second élément de propriété (index 1) dans la liste a <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (fabricant) et <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (tableau d’octets encodé en ASCII). L’exemple de code affiche la valeur de cet élément de propriété.  
  
 Le code produit une sortie similaire à ce qui suit :  
 
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
  
### <a name="code"></a>Code  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 L’exemple précédent est conçu pour une utilisation avec Windows Forms et nécessite <xref:System.Windows.Forms.PaintEventArgs> `e`, qui est un paramètre de la <xref:System.Windows.Forms.Control.Paint> Gestionnaire d’événements. Gérer le formulaire <xref:System.Windows.Forms.Control.Paint> événements et collez ce code dans le Gestionnaire d’événements paint. Vous devez remplacer `FakePhoto.jpg` avec un nom de l’image et le chemin d’accès valide sur votre système et à importer le `System.Drawing.Imaging` espace de noms.  
  
## <a name="see-also"></a>Voir aussi

- [Images, bitmaps et métafichiers](images-bitmaps-and-metafiles.md)
- [Utilisation des images, bitmaps, icônes et métafichiers](working-with-images-bitmaps-icons-and-metafiles.md)
