---
title: Types de bitmaps
ms.date: 03/30/2017
helpviewer_keywords:
- jpeg files
- TIFF files
- gif files
- Graphics Interchange Format
- Joint Photographic Experts Group
- .jpeg files
- .gif files
- graphics [Windows Forms], file formats
- images [Windows Forms], file formats
- Portable Network Graphics
- .bmp files
- EXIF file format
- PNG files
- pictures [Windows Forms], file formats
- Tag Image File Format
- bitmaps [Windows Forms], file format
- Exchangeable Image File
ms.assetid: 6be085a2-2c13-47c8-b80a-c18b32777d8d
ms.openlocfilehash: e678195e96aea881777c44ab14bb2e56aef015bb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505294"
---
# <a name="types-of-bitmaps"></a>Types de bitmaps
Une image bitmap est un tableau de bits qui spécifient la couleur de chaque pixel dans un tableau rectangulaire de pixels. Le nombre de bits associés à un pixel détermine le nombre de couleurs qui peuvent être affectés à ce pixel. Par exemple, si chaque pixel est représenté par 4 bits, puis un pixel donné peut avoir une des 16 couleurs différentes (2 ^ 4 = 16). Le tableau suivant présente quelques exemples du nombre de couleurs qui peuvent être attribués à un pixel représenté par un nombre donné de bits.  
  
|Bits par pixel|Nombre de couleurs qui peuvent être affectés à un pixel|  
|--------------------|------------------------------------------------------|  
|1|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 Les fichiers de disque qui stockent généralement les bitmaps contiennent un ou plusieurs blocs d’informations qui stockent des informations telles que le nombre de bits par pixel, nombre de pixels dans chaque ligne et nombre de lignes dans le tableau. Un tel fichier peut également contenir une table des couleurs (parfois appelée une palette de couleurs). Une table des couleurs mappe les nombres dans la bitmap à des couleurs spécifiques. L’illustration suivante montre une image agrandie avec sa table de bitmap et la couleur. Chaque pixel est représenté par un nombre de 4 bits, il y a 2 ^ 4 = 16 couleurs dans la table des couleurs. Chaque couleur de la table est représenté par un nombre de 24 bits : 8 bits pour le rouge, 8 bits pour le vert et 8 bits pour le bleu. Les nombres sont affichés au format hexadécimal (base 16) : A = 10, B = 11, C = 12, D = 13, E = 14, F = 15.  
  
 ![Exemple de bitmap](./media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 Examinons le pixel dans la ligne 3, colonne 5 de l’image. Le numéro correspondant dans la bitmap est 1. La table des couleurs indique que le nombre 1 représente la couleur rouge. Toutes les entrées dans la ligne du haut de la bitmap seront 3. La table des couleurs indique que 3 représente tous les pixels dans la ligne du haut de l’image sont en bleus.  
  
> [!NOTE]
>  Certaines images bitmap sont stockées au format de bas en haut. les chiffres dans la première ligne de la bitmap correspondent aux pixels de la ligne inférieure de l’image.  
  
 Une image bitmap qui stocke des index dans une table des couleurs est appelée une bitmap indexés de palette. Certaines bitmaps n’ont pas besoin d’une table des couleurs. Par exemple, si une bitmap utilise 24 bits par pixel, elle peut stocker les couleurs elles-mêmes plutôt que des index dans une table des couleurs. L’illustration suivante montre une bitmap qui stocke directement les couleurs (24 bits par pixel) au lieu d’utiliser une table des couleurs. L’illustration montre également une vue agrandie de l’image correspondante. Dans l’image bitmap, FFFFFF représente le blanc, FF0000 représente rouge, 00FF00 le vert et 0000FF représente bleu.  
  
 ![Exemple de bitmap](./media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>Formats de fichiers graphiques  
 Il existe de nombreux formats standards pour enregistrer des bitmaps dans les fichiers de disque. GDI + prend en charge le fichier graphique formats décrits dans les paragraphes suivants.  
  
### <a name="bmp"></a>BMP  
 BMP est un format standard utilisé par Windows pour stocker des images indépendantes du périphérique et indépendant des applications. Le nombre de bits par pixel (1, 4, 8, 15, 24, 32 ou 64) pour un fichier BMP donné est spécifié dans un en-tête de fichier. Fichiers BMP dotés de 24 bits par pixel sont courants. Fichiers BMP sont généralement pas compressés et, par conséquent, ne sont pas adaptés pour le transfert sur Internet.  
  
### <a name="graphics-interchange-format-gif"></a>GIF (Graphics Interchange Format)  
 GIF est un format commun pour les images qui apparaissent sur les pages Web. Fichiers GIF fonctionnent bien pour les dessins, des images avec des blocs de couleur unie et des images avec la netteté des limites entre les couleurs. Ils sont compressés, mais aucune information n’est perdue dans le processus de compression ; une image décompressée est exactement le même que l’original. Une couleur dans un fichier GIF peut être désignée comme étant transparents, afin que l’image aura la couleur d’arrière-plan de n’importe quelle page Web qui l’affiche. Une séquence d’images au format GIF peut être stockée dans un seul fichier pour former une image GIF animée. Fichiers GIF stockent au maximum 8 bits par pixel, ils sont limités à 256 couleurs.  
  
### <a name="joint-photographic-experts-group-jpeg"></a>Joint Photographic Experts Group (JPEG)  
 JPEG est une méthode de compression qui fonctionne bien pour les scènes naturelles telles que des photographies numérisées. Certaines informations sont perdues dans le processus de compression, mais souvent la perte est imperceptible pour le œil humain. Fichiers JPEG stockent 24 bits par pixel, ce qui leur permet d’afficher plus de 16 millions de couleurs. Fichiers JPEG ne gèrent pas la transparence ou une animation.  
  
 Le niveau de compression dans des images JPEG est configurable, mais les niveaux de compression élevés (fichiers plus petits) entraînent une perte de plus d’informations. Un taux de compression de 20:1 produit souvent une image qui le œil humain recherche difficile à distinguer de l’original. L’illustration suivante montre une image BMP et deux images JPEG compressées à partir de cette image BMP. La première image JPEG a un taux de compression de 4:1 et le deuxième JPEG a un taux de compression d’environ 8:1.  
  
 ![Exemples de FileType](./media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 Compression JPEG ne pas fonctionnent bien pour les dessins, des blocs de couleur unie et des limites. L’illustration suivante montre une BMP, ainsi que les deux images JPEG et GIF. Les images JPEG et l’image GIF ont été compressées à partir de la BMP. Le taux de compression est 4:1 pour l’image GIF, 4:1 pour la plus petite image JPEG et 8:3 pour la plus grande image JPEG. Notez que l’image GIF conserve la netteté des limites le long des lignes, mais les images JPEG ont tendance à brouiller les limites.  
  
 ![Filetypes](./media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG est un schéma de compression, pas un format de fichier. JPEG File Interchange Format (JFIF) est un format de fichier couramment utilisé pour stocker et transférer les images qui ont été compressés selon le modèle JPEG. Les fichiers JFIF affichés par les navigateurs Web utilisent l’extension .jpg.  
  
### <a name="exchangeable-image-file-exif"></a>Exchangeable Image File (EXIF)  
 EXIF est un format de fichier utilisé pour les photographies capturées par les appareils photo numériques. Un fichier EXIF contient une image qui est compressée conformément à la spécification JPEG. Un fichier EXIF contient également des informations sur la photographie (date de prise, vitesse d’obturation, temps d’exposition et ainsi de suite) et des informations sur l’appareil photo (fabricant, modèle et ainsi de suite).  
  
### <a name="portable-network-graphics-png"></a>PNG (Portable Network Graphics)  
 Le format PNG conserve tous les avantages du format GIF, mais fournit également des fonctionnalités au-delà de celles de GIF. Comme les fichiers GIF, PNG sont compressés sans perte d’informations. Fichiers PNG peuvent stocker des couleurs avec 8, 24, ou 48 bits par pixel et des nuances de gris avec 1, 2, 4, 8 ou 16 bits par pixel. En revanche, les fichiers GIF peuvent utiliser seulement 1, 2, 4 ou 8 bits par pixel. Un fichier PNG peut également stocker une valeur alpha pour chaque pixel, qui spécifie le degré auquel la couleur de ce pixel est fusionnée avec la couleur d’arrière-plan.  
  
 PNG améliore dans sa capacité à afficher progressivement une image GIF (autrement dit, pour afficher des approximations de plus en plus de l’image en tant qu’il arrive sur une connexion réseau). Fichiers PNG peuvent contenir des informations de correction de couleur et de correction gamma afin que les images peuvent être rendus avec précision sur un large éventail de périphériques d’affichage.  
  
### <a name="tag-image-file-format-tiff"></a>Tag Image File Format (TIFF)  
 TIFF est un format flexible et extensible qui est pris en charge par un large éventail de plates-formes et applications de traitement d’image. Fichiers TIFF peuvent stocker des images avec un nombre arbitraire de bits par pixel et utilisent différents algorithmes de compression. Plusieurs images peuvent être stockées dans un seul fichier TIFF à plusieurs pages. Informations relatives à l’image (marque de scanneur, ordinateur hôte, type de compression, orientation, échantillons par pixel et ainsi de suite) peuvent être stockées dans le fichier et organisées à l’aide de balises. Le format TIFF peut être étendu en fonction des besoins par l’approbation et l’ajout de nouvelles balises.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Image?displayProperty=nameWithType>
- <xref:System.Drawing.Bitmap?displayProperty=nameWithType>
- <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>
- [Images, bitmaps et métafichiers](images-bitmaps-and-metafiles.md)
- [Utilisation des images, bitmaps, icônes et métafichiers](working-with-images-bitmaps-icons-and-metafiles.md)
