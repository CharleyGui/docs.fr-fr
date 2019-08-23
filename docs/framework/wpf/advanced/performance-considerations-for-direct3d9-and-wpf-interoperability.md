---
title: Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
ms.openlocfilehash: 02a91c1824c5d6374f37b0af66a3308d33210c4a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932492"
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF
Vous pouvez héberger le contenu Direct3D9 à <xref:System.Windows.Interop.D3DImage> l’aide de la classe. L’hébergement de contenu Direct3D9 peut affecter les performances de votre application. Cette rubrique décrit les meilleures pratiques pour optimiser les performances lors de l’hébergement de contenu Direct3D9 dans une application Windows Presentation Foundation (WPF). Ces meilleures pratiques incluent l’utilisation <xref:System.Windows.Interop.D3DImage> de et des meilleures pratiques lorsque vous utilisez Windows Vista, Windows XP et des affichages à plusieurs écrans.  
  
> [!NOTE]
> Pour obtenir des exemples de code qui illustrent ces meilleures pratiques, consultez [interopérabilité WPF et Direct3D9](wpf-and-direct3d9-interoperation.md).  
  
## <a name="use-d3dimage-sparingly"></a>Utiliser D3DImage avec modération  
 Le contenu Direct3D9 hébergé dans <xref:System.Windows.Interop.D3DImage> une instance n’est pas restitué aussi rapidement que dans une application Direct3D pure. La copie de la surface et le vidage du tampon de commande peuvent être des opérations coûteuses. À mesure que le <xref:System.Windows.Interop.D3DImage> nombre d’instances augmente, le vidage se produit et les performances diminuent. Par conséquent, vous devez <xref:System.Windows.Interop.D3DImage> utiliser la modération.  
  
## <a name="best-practices-on-windows-vista"></a>Meilleures pratiques sur Windows Vista  
 Pour obtenir de meilleures performances sur Windows Vista avec un affichage configuré pour utiliser le modèle WDDM (Windows Display Driver Model), créez votre surface Direct3D9 sur `IDirect3DDevice9Ex` un appareil. Cela active le partage de surface. La carte vidéo doit prendre en `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` charge `D3DCAPS2_CANSHARERESOURCE` les fonctionnalités du pilote et sur Windows Vista. Tous les autres paramètres entraînent la copie de la surface par le biais d’un logiciel, ce qui réduit considérablement les performances.  
  
> [!NOTE]
> Si Windows Vista a un affichage configuré pour utiliser le modèle de pilote d’affichage (XDDM) de Windows XP, la surface est toujours copiée via un logiciel, quels que soient les paramètres. Avec les paramètres et la carte vidéo appropriés, vous obtiendrez de meilleures performances sur Windows Vista lorsque vous utilisez le WDDM, car des copies superficielles sont effectuées sur le matériel.  
  
## <a name="best-practices-on-windows-xp"></a>Meilleures pratiques sur Windows XP  
 Pour de meilleures performances sur Windows XP, qui utilise le modèle de pilote d’affichage Windows XP (XDDM), créez une surface verrouillable qui se comporte correctement `IDirect3DSurface9::GetDC` lorsque la méthode est appelée. En interne, la `BitBlt` méthode transfère la surface entre les appareils dans le matériel. La `GetDC` méthode fonctionne toujours sur les surfaces XRGB. Toutefois, si l’ordinateur client exécute Windows XP avec SP3 ou SP2, et si le client possède également le correctif logiciel pour la fonctionnalité de fenêtre en couche, cette méthode fonctionne uniquement sur les surfaces ARVB. La carte vidéo doit prendre en `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` charge la fonctionnalité du pilote.  
  
 Une profondeur d’affichage du bureau 16 bits peut réduire considérablement les performances. Un bureau 32 bits est recommandé.  
  
 Si vous développez pour Windows Vista et Windows XP, testez les performances sur Windows XP. Le manque de mémoire vidéo sur Windows XP est un problème. En outre, <xref:System.Windows.Interop.D3DImage> sur Windows XP utilise davantage de mémoire vidéo et de bande passante que le WDDM Windows Vista, en raison d’une copie supplémentaire de la mémoire vidéo. Par conséquent, vous pouvez vous attendre à ce que les performances soient moins bonnes sur Windows XP que sur Windows Vista pour le même matériel vidéo.  
  
> [!NOTE]
> XDDM est disponible sur Windows XP et Windows Vista. Toutefois, le WDDM est disponible uniquement sur Windows Vista.  
  
## <a name="general-best-practices"></a>Meilleures pratiques générales  
 Lorsque vous créez l’appareil, utilisez l' `D3DCREATE_MULTITHREADED` indicateur de création. Cela réduit les performances, mais le système de rendu WPF appelle les méthodes sur cet appareil à partir d’un autre thread. Veillez à suivre correctement le protocole de verrouillage, afin que deux threads n’accèdent pas à l’appareil en même temps.  
  
 Si votre rendu est effectué sur un thread managé WPF, il est fortement recommandé de créer l’appareil avec l' `D3DCREATE_FPU_PRESERVE` indicateur de création. Sans ce paramètre, le rendu D3D peut réduire la précision des opérations WPF double précision et introduire des problèmes de rendu.  
  
 La mosaïque <xref:System.Windows.Interop.D3DImage> a est rapide, à moins que vous ne décarreaux une surface non pow2 sans la prise en charge <xref:System.Windows.Media.DrawingBrush> matérielle, ou si <xref:System.Windows.Interop.D3DImage>vous VIGNETTEZ un ou <xref:System.Windows.Media.VisualBrush> qui contient un.  
  
## <a name="best-practices-for-multi-monitor-displays"></a>Meilleures pratiques pour les affichages à plusieurs écrans  
 Si vous utilisez un ordinateur équipé de plusieurs moniteurs, vous devez suivre les meilleures pratiques décrites précédemment. Il existe également des considérations supplémentaires sur les performances pour une configuration à plusieurs écrans.  
  
 Lorsque vous créez la mémoire tampon d’arrière-plan, elle est créée sur un appareil et un adaptateur spécifiques, mais WPF peut afficher le tampon d’affichage sur n’importe quel adaptateur. La copie sur les adaptateurs pour mettre à jour le tampon d’avant peut être très coûteuse. Sur Windows Vista qui est configuré pour utiliser le WDDM avec plusieurs cartes vidéo et avec un `IDirect3DDevice9Ex` périphérique, si le tampon d’entrée est sur un autre adaptateur mais toujours sur la même carte vidéo, il n’y a aucune baisse des performances. Toutefois, sur Windows XP et le XDDM avec plusieurs cartes vidéo, il y a une baisse importante des performances lorsque le tampon d’avant est affiché sur un autre adaptateur que la mémoire tampon d’arrière-plan. Pour plus d’informations, consultez [interopérabilité WPF et Direct3D9](wpf-and-direct3d9-interoperation.md).  
  
## <a name="performance-summary"></a>Résumé des performances  
 Le tableau suivant montre les performances de la mise à jour de la mémoire tampon avant en fonction du système d’exploitation, du format de pixel et de la fonctionnalité de verrouillage en surface. La mémoire tampon d’arrière-plan et la mémoire tampon d’arrière-plan sont supposées être sur le même adaptateur. En fonction de la configuration de l’adaptateur, les mises à jour matérielles sont généralement beaucoup plus rapides que les mises à jour logicielles.  
  
|Format de pixel de surface|Windows Vista, WDDM et 9Ex|Autres configurations de Windows Vista|Windows XP SP3 ou SP2 avec correctif logiciel|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (non verrouillable)|**Mise à jour matérielle**|Mise à jour logicielle|Mise à jour logicielle|Mise à jour logicielle|  
|D3DFMT_X8R8G8B8 (verrouillable)|**Mise à jour matérielle**|Mise à jour logicielle|**Mise à jour matérielle**|**Mise à jour matérielle**|  
|D3DFMT_A8R8G8B8 (non verrouillable)|**Mise à jour matérielle**|Mise à jour logicielle|Mise à jour logicielle|Mise à jour logicielle|  
|D3DFMT_A8R8G8B8 (verrouillable)|**Mise à jour matérielle**|Mise à jour logicielle|**Mise à jour matérielle**|Mise à jour logicielle|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.D3DImage>
- [Interopérabilité WPF et Direct3D9](wpf-and-direct3d9-interoperation.md)
- [Procédure pas à pas : Création de contenu Direct3D9 pour l’hébergement dans WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [Procédure pas à pas : Hébergement de contenu Direct3D9 dans WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
