---
title: Types de bitmaps
description: En savoir plus sur les types de bitmaps et les formats de fichiers graphiques GDI+ pris en charge, notamment BMP, JPG, GIF, PNG et TIFF.
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
ms.openlocfilehash: 09b74ef476467b0bba5aac1f58db278b3898ef17
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174677"
---
# <a name="types-of-bitmaps"></a>Types de bitmaps
Une image bitmap est un tableau de bits qui spécifient la couleur de chaque pixel dans un tableau rectangulaire de pixels. Le nombre de bits consacrés à un pixel individuel détermine le nombre de couleurs qui peuvent être affectées à ce pixel. Par exemple, si chaque pixel est représenté par 4 bits, un pixel donné peut se voir assigner l’une des 16 couleurs différentes (2 ^ 4 = 16). Le tableau suivant présente quelques exemples du nombre de couleurs qui peuvent être assignées à un pixel représenté par un nombre donné de bits.  
  
|Bits par pixel|Nombre de couleurs pouvant être affectées à un pixel|  
|--------------------|------------------------------------------------------|  
|1|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 Les fichiers de disque qui stockent des bitmaps contiennent généralement un ou plusieurs blocs d’informations qui stockent des informations telles que le nombre de bits par pixel, le nombre de pixels dans chaque ligne et le nombre de lignes dans le tableau. Un tel fichier peut également contenir une table des couleurs (parfois appelée palette de couleurs). Une table des couleurs associe les nombres de la bitmap à des couleurs spécifiques. L’illustration suivante montre une image agrandie ainsi que ses tables bitmap et couleur. Chaque pixel étant représenté par un nombre de 4 bits, il y a 2 ^ 4 = 16 couleurs dans la table des couleurs. Chaque couleur de la table est représentée par un nombre de 24 bits : 8 bits pour le rouge, 8 bits pour le vert et 8 bits pour le bleu. Les nombres sont affichés au format hexadécimal (base 16) : A = 10, B = 11, C = 12, D = 13, E = 14, F = 15.  
  
 ![Exemple de bitmap](./media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 Examinez le pixel de la ligne 3, colonne 5 de l’image. Le nombre correspondant dans la bitmap est 1. La table des couleurs nous dit que 1 représente la couleur rouge pour que le pixel soit rouge. Toutes les entrées dans la ligne supérieure de la bitmap sont 3. La table des couleurs nous dit que 3 représente le bleu, donc tous les pixels de la ligne supérieure de l’image sont bleus.  
  
> [!NOTE]
> Certaines images bitmap sont stockées dans un format ascendant. les nombres de la première ligne de l’image bitmap correspondent aux pixels de la ligne inférieure de l’image.  
  
 Une bitmap qui stocke des index dans une table de couleurs est appelée bitmap indexée par palette. Certaines images bitmap n’ont pas besoin d’une table des couleurs. Par exemple, si une bitmap utilise 24 bits par pixel, cette bitmap peut stocker les couleurs elles-mêmes plutôt que des index dans une table de couleurs. L’illustration suivante montre une image bitmap qui stocke les couleurs directement (24 bits par pixel) au lieu d’utiliser une table des couleurs. L’illustration montre également une vue agrandie de l’image correspondante. Dans la bitmap, FFFFFF représente White, FF0000 représente Red, 00FF00 représente Green et 0000FF représente Blue.  
  
 ![Exemple de bitmap](./media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>Formats de fichiers graphiques  
 Il existe de nombreux formats standard pour enregistrer des bitmaps dans des fichiers de disque. GDI+ prend en charge les formats de fichiers graphiques décrits dans les paragraphes suivants.  
  
### <a name="bmp"></a>BMP  
 BMP est un format standard utilisé par Windows pour stocker des images indépendantes des appareils et des applications. Le nombre de bits par pixel (1, 4, 8, 15, 24, 32 ou 64) pour un fichier BMP donné est spécifié dans un en-tête de fichier. Les fichiers BMP avec 24 bits par pixel sont courants. Les fichiers BMP ne sont généralement pas compressés et, par conséquent, ne sont pas bien adaptés au transfert sur Internet.  
  
### <a name="graphics-interchange-format-gif"></a>GIF (Graphics Interchange Format)  
 GIF est un format courant pour les images qui apparaissent sur des pages Web. Les images gif fonctionnent bien pour les dessins en courbes, les images avec des blocs de couleur unie et les images avec des limites nettes entre les couleurs. Les images gif sont compressées, mais aucune information n’est perdue dans le processus de compression. une image décompressée est exactement la même que l’image d’origine. Une couleur dans un fichier GIF peut être désignée comme transparente, afin que l’image ait la couleur d’arrière-plan d’une page Web qui l’affiche. Une séquence d’images GIF peut être stockée dans un fichier unique pour former une image GIF animée. Les images gif sont stockées au maximum 8 bits par pixel. elles sont donc limitées à 256 couleurs.  
  
### <a name="joint-photographic-experts-group-jpeg"></a>Joint Photographic Experts Group (JPEG)  
 JPEG est un schéma de compression qui fonctionne bien pour les scènes naturelles telles que les photographies numérisées. Certaines informations sont perdues dans le processus de compression, mais la perte est souvent imperceptible à l’oeil humain. Les fichiers JPEG stockent 24 bits par pixel, de sorte qu’ils peuvent afficher plus de 16 millions couleurs. Les fichiers JPEG ne prennent pas en charge la transparence ou l’animation.  
  
 Le niveau de compression des images JPEG est configurable, mais les niveaux de compression plus élevés (fichiers plus petits) entraînent une perte de données. Un taux de compression de 20:1 produit souvent une image que l’oeil humain trouve difficile à distinguer de l’original. L’illustration suivante montre une image BMP et deux images JPEG qui ont été compressées à partir de cette image BMP. Le premier JPEG a un taux de compression de 4:1 et le second JPEG a un ratio de compression d’environ 8:1.  
  
 ![Exemples de types de fichiers](./media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 La compression JPEG ne fonctionne pas correctement pour les dessins en ligne, les blocs de couleur unie et les limites nettes. L’illustration suivante montre un fichier BMP avec deux images JPEG et une image GIF. Les fichiers JPEG et GIF ont été compressés à partir du BMP. Le taux de compression est 4:1 pour le GIF, 4:1 pour le JPEG plus petit et 8:3 pour le JPEG plus grand. Notez que l’image GIF maintient les limites nettes le long des lignes, mais les JPEG ont tendance à brouiller les limites.  
  
 ![Types de fichiers](./media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG est un schéma de compression, pas un format de fichier. Le format d’échange de fichiers JPEG (JFIF) est un format de fichier couramment utilisé pour le stockage et le transfert d’images qui ont été compressées conformément au schéma JPEG. Les fichiers JFIF affichés par les navigateurs Web utilisent l’extension. jpg.  
  
### <a name="exchangeable-image-file-exif"></a>Fichier image d’échange (EXIF)  
 EXIF est un format de fichier utilisé pour les photographies capturées par les appareils photo numériques. Un fichier EXIF contient une image compressée conformément à la spécification JPEG. Un fichier EXIF contient également des informations sur la photographie (date de prise, vitesse d’obturation, temps d’exposition, etc.) et des informations sur l’appareil photo (fabricant, modèle, etc.).  
  
### <a name="portable-network-graphics-png"></a>PNG (Portable Network Graphics)  
 Le format PNG conserve un grand nombre des avantages du format GIF, mais fournit également des fonctionnalités au-delà de celles de GIF. À l’instar des fichiers GIF, les fichiers PNG sont compressés sans perte d’informations. Les fichiers PNG peuvent stocker des couleurs avec 8, 24 ou 48 bits par pixel et des nuances de gris avec 1, 2, 4, 8 ou 16 bits par pixel. En revanche, les fichiers GIF peuvent uniquement utiliser 1, 2, 4 ou 8 bits par pixel. Un fichier PNG peut également stocker une valeur alpha pour chaque pixel, qui spécifie le degré auquel la couleur de ce pixel est fusionnée avec la couleur d’arrière-plan.  
  
 PNG améliore le format GIF dans sa capacité à afficher progressivement une image (autrement dit, à afficher des approximations plus performantes de l’image lors de son arrivée sur une connexion réseau). Les fichiers PNG peuvent contenir des informations de correction gamma et de correction des couleurs afin que les images puissent être rendues avec précision sur divers périphériques d’affichage.  
  
### <a name="tag-image-file-format-tiff"></a>TIFF (tag image file format)  
 TIFF est un format flexible et extensible qui est pris en charge par un large éventail de plateformes et d’applications de traitement d’images. Les fichiers TIFF peuvent stocker des images avec un nombre arbitraire de bits par pixel et utiliser un large éventail d’algorithmes de compression. Plusieurs images peuvent être stockées dans un seul fichier TIFF de plusieurs pages. Les informations relatives à l’image (marque du scanneur, ordinateur hôte, type de compression, orientation, échantillons par pixel, etc.) peuvent être stockées dans le fichier et réorganisées à l’aide de balises. Le format TIFF peut être étendu en fonction des besoins de l’approbation et de l’ajout de nouvelles balises.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Image?displayProperty=nameWithType>
- <xref:System.Drawing.Bitmap?displayProperty=nameWithType>
- <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>
- [Images, bitmaps et métafichiers](images-bitmaps-and-metafiles.md)
- [Utilisation des images, bitmaps, icônes et métafichiers](working-with-images-bitmaps-icons-and-metafiles.md)
