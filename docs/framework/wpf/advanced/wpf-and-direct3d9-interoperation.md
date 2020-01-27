---
title: Interopérabilité WPF et Direct3D9
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
ms.openlocfilehash: 9ec83c48052e1ef29bb91a6b40b7c76f671bb99f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735182"
---
# <a name="wpf-and-direct3d9-interoperation"></a>Interopérabilité WPF et Direct3D9
Vous pouvez inclure du contenu Direct3D9 dans une application Windows Presentation Foundation (WPF). Cette rubrique explique comment créer du contenu Direct3D9 afin qu’il interagisse efficacement avec WPF.  
  
> [!NOTE]
> Quand vous utilisez du contenu Direct3D9 dans WPF, vous devez également réfléchir aux performances. Pour plus d’informations sur la façon d’optimiser les performances, consultez [Considérations sur les performances de l’interopérabilité entre Direct3D9 et WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Mémoires tampons d’affichage  
 La classe <xref:System.Windows.Interop.D3DImage> gère deux mémoires tampons d’affichage, appelées *mémoire tampon d’arrière* - *plan et mémoire tampon*d’arrière-plan. La mémoire tampon d’arrière-plan est votre surface Direct3D9. Les modifications apportées à la mémoire tampon d’arrière-plan sont copiées par progression vers la mémoire tampon d’avance lorsque vous appelez la méthode <xref:System.Windows.Interop.D3DImage.Unlock%2A>.  
  
 L’illustration suivante montre la relation entre la mémoire tampon d’arrière-plan et la mémoire tampon d’arrière-plan.  
  
 ![Mémoires tampons d’affichage D3DImage](./media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Création d’appareils Direct3D9  
 Pour afficher le contenu Direct3D9, vous devez créer un appareil Direct3D9. Il existe deux objets Direct3D9 que vous pouvez utiliser pour créer un appareil, `IDirect3D9` et `IDirect3D9Ex`. Utilisez ces objets pour créer des `IDirect3DDevice9` et des appareils `IDirect3DDevice9Ex`, respectivement.  
  
 Créez un appareil en appelant l’une des méthodes suivantes.  
  
- `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
- `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 Sur Windows Vista ou un système d’exploitation ultérieur, utilisez la méthode `Direct3DCreate9Ex` avec un affichage configuré pour utiliser le modèle WDDM (Windows Display Driver Model). Utilisez la méthode `Direct3DCreate9` sur toute autre plateforme.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Disponibilité de la méthode Direct3DCreate9Ex  
 D3d9. dll a la méthode `Direct3DCreate9Ex` uniquement sur Windows Vista ou un système d’exploitation ultérieur. Si vous liez directement la fonction sur Windows XP, votre application ne se charge pas. Pour déterminer si la méthode `Direct3DCreate9Ex` est prise en charge, chargez la DLL et recherchez l’adresse proc. Le code suivant montre comment tester la méthode `Direct3DCreate9Ex`. Pour obtenir un exemple de code complet, consultez [procédure pas à pas : création de contenu Direct3D9 pour l’hébergement dans WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>Création HWND  
 La création d’un appareil requiert un HWND. En général, vous créez un HWND factice à utiliser par Direct3D9. L’exemple de code suivant montre comment créer un HWND factice.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Paramètres présents  
 La création d’un appareil nécessite également un struct `D3DPRESENT_PARAMETERS`, mais seuls quelques paramètres sont importants. Ces paramètres sont choisis pour réduire l’encombrement mémoire.  
  
 Définissez les champs `BackBufferHeight` et `BackBufferWidth` sur 1. Si vous leur attribuez la valeur 0, elles sont définies sur les dimensions du HWND.  
  
 Définissez toujours les indicateurs `D3DCREATE_MULTITHREADED` et `D3DCREATE_FPU_PRESERVE` pour empêcher l’endommagement de la mémoire utilisée par Direct3D9 et empêcher Direct3D9 de modifier les paramètres FPU.  
  
 Le code suivant montre comment initialiser le struct `D3DPRESENT_PARAMETERS`.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Création de la cible de rendu de la mémoire tampon d’arrière-plan  
 Pour afficher le contenu Direct3D9 dans un <xref:System.Windows.Interop.D3DImage>, vous créez une surface Direct3D9 et l’attribuez en appelant la méthode <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
### <a name="verifying-adapter-support"></a>Vérification de la prise en charge des adaptateurs  
 Avant de créer une surface, vérifiez que tous les adaptateurs prennent en charge les propriétés de surface dont vous avez besoin. Même si vous affichez un seul adaptateur, la fenêtre WPF peut s’afficher sur n’importe quel adaptateur du système. Vous devez toujours écrire du code Direct3D9 qui gère les configurations à plusieurs adaptateurs, et vous devez vérifier tous les adaptateurs pour la prise en charge, car WPF peut déplacer l’aire entre les adaptateurs disponibles.  
  
 L’exemple de code suivant montre comment vérifier tous les adaptateurs du système pour la prise en charge de Direct3D9.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Création de la surface  
 Avant de créer une surface, vérifiez que les fonctionnalités de l’appareil prennent en charge de bonnes performances sur le système d’exploitation cible. Pour plus d’informations, consultez [Considérations sur les performances pour l’interopérabilité entre Direct3D9 et WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Une fois que vous avez vérifié les fonctionnalités de l’appareil, vous pouvez créer l’aire. L’exemple de code suivant montre comment créer la cible de rendu.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>WDDM  
 Sur les systèmes d’exploitation Windows Vista et versions ultérieures, qui sont configurés pour utiliser le WDDM, vous pouvez créer une texture de cible de rendu et passer la surface de niveau 0 à la méthode <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>. Cette approche n’est pas recommandée sur Windows XP, car vous ne pouvez pas créer une texture de cible de rendu verrouillable et les performances seront réduites.  
  
## <a name="handling-device-state"></a>Gestion de l’état de l’appareil  
 La classe <xref:System.Windows.Interop.D3DImage> gère deux mémoires tampons d’affichage, appelées *mémoire tampon d’arrière* - *plan et mémoire tampon*d’arrière-plan. La mémoire tampon d’arrière-plan est votre surface Direct3D.  Les modifications apportées à la mémoire tampon d’arrière-plan sont copiées par progression vers la mémoire tampon d’origine lorsque vous appelez la méthode <xref:System.Windows.Interop.D3DImage.Unlock%2A>, où elle est affichée sur le matériel. Parfois, le tampon d’avant devient indisponible. Ce manque de disponibilité peut être dû à un verrouillage d’écran, à des applications Direct3D exclusives en plein écran, à une commutation utilisateur ou à d’autres activités système. Lorsque cela se produit, votre application WPF est notifiée en gérant l’événement <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged>.  La façon dont votre application répond à la mémoire tampon d’arrière-plan devient indisponible varie selon que WPF est activé pour revenir au rendu logiciel. La méthode <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> a une surcharge qui prend un paramètre qui spécifie si WPF revient au rendu logiciel.  
  
 Quand vous appelez la surcharge <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> ou que vous appelez la surcharge de <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> avec le paramètre `enableSoftwareFallback` défini sur `false`, le système de rendu libère sa référence à la mémoire tampon d’arrière-plan lorsque la mémoire tampon d’arrière-plan devient indisponible et rien ne s’affiche. Lorsque le tampon d’avant est à nouveau disponible, le système de rendu déclenche l’événement <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> pour notifier votre application WPF.  Vous pouvez créer un gestionnaire d’événements pour l’événement <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> pour redémarrer le rendu avec une surface Direct3D valide. Pour redémarrer le rendu, vous devez appeler <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
 Quand vous appelez la surcharge <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> avec le paramètre `enableSoftwareFallback` défini sur `true`, le système de rendu conserve sa référence à la mémoire tampon d’arrière-plan lorsque la mémoire tampon d’arrière-plan devient indisponible. il n’est donc pas nécessaire d’appeler <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> lorsque le tampon d’avant est à nouveau disponible.  
  
 Lorsque le rendu logiciel est activé, il peut y avoir des situations où l’appareil de l’utilisateur devient indisponible, mais le système de rendu conserve une référence à la surface Direct3D. Pour vérifier si un appareil Direct3D9 n’est pas disponible, appelez la méthode `TestCooperativeLevel`. Pour vérifier qu’un appareil Direct3D9Ex appelle la méthode `CheckDeviceState`, parce que la méthode `TestCooperativeLevel` est déconseillée et retourne toujours Success. Si l’appareil de l’utilisateur n’est plus disponible, appelez <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> pour libérer la référence du WPF à la mémoire tampon d’arrière-plan.  Si vous devez réinitialiser votre appareil, appelez <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> avec le paramètre `backBuffer` défini sur `null`, puis appelez à nouveau <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> avec `backBuffer` défini sur une surface Direct3D valide.  
  
 Appelez la méthode `Reset` pour récupérer à partir d’un appareil non valide uniquement si vous implémentez la prise en charge de plusieurs adaptateurs. Dans le cas contraire, libérez toutes les interfaces Direct3D9, puis recréez-les entièrement. Si la disposition de l’adaptateur a changé, les objets Direct3D9 créés avant la modification ne sont pas mis à jour.  
  
## <a name="handling-resizing"></a>Gérer le redimensionnement  
 Si un <xref:System.Windows.Interop.D3DImage> est affiché dans une résolution autre que sa taille native, il est mis à l’échelle en fonction du <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>actuel, sauf que <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> remplace <xref:System.Windows.Media.BitmapScalingMode.Fant>.  
  
 Si vous avez besoin d’une meilleure fidélité, vous devez créer une nouvelle surface lorsque le conteneur du <xref:System.Windows.Interop.D3DImage> change de taille.  
  
 Il existe trois approches possibles pour gérer le redimensionnement.  
  
- Participez au système de disposition et créez une nouvelle surface lorsque la taille change. Ne créez pas trop de surfaces, car vous risquez d’épuiser ou de fragmenter la mémoire vidéo.  
  
- Attendez qu’un événement de redimensionnement n’ait pas eu lieu pendant une période fixe pour créer la nouvelle surface.  
  
- Créez un <xref:System.Windows.Threading.DispatcherTimer> qui vérifie les dimensions de conteneur plusieurs fois par seconde.  
  
## <a name="multi-monitor-optimization"></a>Optimisation de plusieurs moniteurs  
 Une baisse significative des performances peut se produire lorsque le système de rendu déplace un <xref:System.Windows.Interop.D3DImage> vers un autre moniteur.  
  
 Sur WDDM, à condition que les moniteurs se trouvent sur la même carte vidéo et que vous utilisiez `Direct3DCreate9Ex`, les performances ne sont pas réduites. Si les moniteurs se trouvent sur des cartes vidéo distinctes, les performances sont réduites. Sur Windows XP, les performances sont toujours réduites.  
  
 Lorsque le <xref:System.Windows.Interop.D3DImage> passe à un autre moniteur, vous pouvez créer une nouvelle surface sur l’adaptateur correspondant pour restaurer de bonnes performances.  
  
 Pour éviter la perte de performances, écrivez du code spécifiquement pour le cas de plusieurs écrans. La liste suivante illustre une façon d’écrire du code à plusieurs écrans.  
  
1. Recherchez un point de la <xref:System.Windows.Interop.D3DImage> dans l’espace à l’écran avec la méthode `Visual.ProjectToScreen`.  
  
2. Utilisez la méthode GDI `MonitorFromPoint` pour rechercher le moniteur qui affiche le point.  
  
3. Utilisez la méthode `IDirect3D9::GetAdapterMonitor` pour Rechercher l’adaptateur Direct3D9 sur lequel l’analyse est activée.  
  
4. Si l’adaptateur n’est pas le même que l’adaptateur avec la mémoire tampon d’arrière-plan, créez une nouvelle mémoire tampon d’arrière-plan sur le nouvel écran et affectez-la au <xref:System.Windows.Interop.D3DImage> mémoire tampon d’arrière-plan.  
  
> [!NOTE]
> Si le <xref:System.Windows.Interop.D3DImage> passe sur les moniteurs, les performances sont lentes, sauf dans le cas de WDDM et `IDirect3D9Ex` sur le même adaptateur. Il n’existe aucun moyen d’améliorer les performances dans cette situation.  
  
 L’exemple de code suivant montre comment rechercher le moniteur en cours.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 Mettez à jour le moniteur lorsque la taille ou la position du conteneur <xref:System.Windows.Interop.D3DImage> change, ou mettez à jour le moniteur à l’aide d’un `DispatcherTimer` qui se met à jour plusieurs fois par seconde.  
  
## <a name="wpf-software-rendering"></a>Rendu logiciel WPF  
 WPF est rendu de façon synchrone sur le thread d’interface utilisateur dans les logiciels dans les cas suivants.  
  
- Impression  
  
- <xref:System.Windows.Media.Effects.BitmapEffect>  
  
- <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Lorsque l’une de ces situations se produit, le système de rendu appelle la méthode <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> pour copier la mémoire tampon matérielle sur le logiciel. L’implémentation par défaut appelle la méthode `GetRenderTargetData` avec votre surface. Dans la mesure où cet appel se produit en dehors du modèle de verrouillage/déverrouillage, il peut échouer. Dans ce cas, la méthode `CopyBackBuffer` retourne `null` et aucune image n’est affichée.  
  
 Vous pouvez substituer la méthode <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A>, appeler l’implémentation de base et, si elle retourne `null`, vous pouvez retourner un espace réservé <xref:System.Windows.Media.Imaging.BitmapSource>.  
  
 Vous pouvez également implémenter votre propre rendu logiciel au lieu d’appeler l’implémentation de base.  
  
> [!NOTE]
> Si WPF effectue un rendu complet dans le logiciel, <xref:System.Windows.Interop.D3DImage> n’est pas affiché, car WPF n’a pas de mémoire tampon d’avant.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Interop.D3DImage>
- [Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [Procédure pas à pas : création de contenu Direct3D9 à héberger dans WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)
- [Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)
