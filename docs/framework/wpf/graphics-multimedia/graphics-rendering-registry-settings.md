---
title: Paramètres du Registre pour le rendu des graphiques
ms.date: 03/30/2017
helpviewer_keywords:
- rendering graphics [WPF], registry settings
- rendering graphics [WPF]
- rendering graphics [WPF], troubleshooting
- troubleshooting graphics rendering [WPF]
- graphics [WPF], rendering
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
ms.openlocfilehash: 85e32c99674cc95f670a4cb483b55865b996cb31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186425"
---
# <a name="graphics-rendering-registry-settings"></a>Paramètres du Registre pour le rendu des graphiques
Cette rubrique fournit une vue d’ensemble des paramètres du Registre pour le rendu des graphiques [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui affectent les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="overview"></a>
## <a name="when-to-use-graphics-rendering-registry-settings"></a>Quand utiliser les paramètres du Registre pour le rendu des graphiques  
 Ces paramètres du Registre sont fournis à des fins de résolution des problèmes, de débogage et de prise en charge du produit. Étant donné que les modifications apportées au Registre affectent toutes applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], votre application ne doit jamais modifier ces clés de Registre automatiquement, ni lors de l’installation.  
  
<a name="xpdmandwddm"></a>
## <a name="what-are-xpdm-and-wddm"></a>Que sont XPDM et WDDM ?  
 Certains paramètres du Registre pour le rendu des graphiques ont des valeurs par défaut différentes selon que votre carte vidéo utilise un pilote XPDM ou WDDM. XPDM est le microsoft Windows XP Display Driver Model et WDDM est le modèle de pilote Windows Display. WDDM est disponible sur les ordinateurs fonctionnant sous Windows Vista et Windows 7. XPDM est disponible sur les ordinateurs fonctionnant sous Windows Vista, Microsoft Windows XP et Microsoft Windows Server 2003. Pour plus d’informations sur WDDM, voir [Windows Display Driver Model (WDDM) Design Guide](/windows-hardware/drivers/display/windows-vista-display-driver-model-design-guide).  
  
<a name="registry_settings"></a>
## <a name="registry-settings"></a>Paramètres du Registre  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit quatre paramètres du Registre pour le contrôle du rendu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
|Paramètre|Description|  
|-------------|-----------------|  
|**Option Désactiver l’accélération matérielle**|Spécifie si l’accélération matérielle doit être activée.|  
|**Valeur d’échantillonnage multiple maximale**|Spécifie le degré de multisampling pour antialiasing contenu 3-D.|  
|**Paramètre Date de pilote vidéo requise**|Spécifie si le système désactive l’accélération matérielle pour les pilotes commercialisés avant novembre 2004.|  
|**Option Utiliser le rastériseur de référence**|Spécifie si [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] doit utiliser le rastériseur de référence.|  
  
 Ces paramètres sont accessibles à tout utilitaire de configuration externe capable de référencer les paramètres du Registre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Ces paramètres peuvent également être créés ou modifiés en accédant directement aux valeurs en utilisant l’éditeur du registre Windows.  
  
<a name="disablehardwareacceleration"></a>
## <a name="disable-hardware-acceleration-option"></a>Option Désactiver l’accélération matérielle  
  
|Clé de Registre|Type de valeur|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 **L’option Désactiver l’accélération matérielle** vous permet de désactiver l’accélération matérielle à des fins de débogage et de test. Lorsque vous voyez des artefacts de rendu dans une application, essayez de désactiver l’accélération matérielle. Si les artefacts disparaissent, le problème peut être lié à votre pilote vidéo.  
  
 **L’option Désactiver l’accélération matérielle** est une valeur DWORD qui est égale à 0 ou à 1. La valeur 1 désactive l’accélération matérielle. La valeur 0 active l’accélération matérielle, à condition que le système soit conforme aux exigences de l’accélération matérielle. Pour plus d’informations, consultez [Couches de rendu graphiques](../advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>
## <a name="maximum-multisample-value"></a>Valeur d’échantillonnage multiple maximale  
  
|Clé de Registre|Type de valeur|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 La **valeur multisample maximale** vous permet d’ajuster la quantité maximale d’anti-analyse de contenu 3D. Utilisez ce niveau pour désactiver l’antialiasing 3D dans Windows Vista.  
  
 La **valeur d’échantillonnage multiple maximale** est une valeur DWORD comprise entre 0 et 16. La valeur 0 spécifie que l’anticrénelage d’échantillonnage multiple du contenu 3D doit être désactivé, et la valeur 16 essaye d’utiliser jusqu’à 16 anticrénelages d’échantillonnage multiple, si cela est pris en charge par la carte vidéo. Méfiez-vous que le réglage de cette valeur clé de registre sur les ordinateurs utilisant des pilotes XPDM entraînera des applications à utiliser une grande quantité de mémoire vidéo supplémentaire, diminuer les performances du rendu 3D, et a le potentiel d’introduire des erreurs de rendu et de stabilité Problèmes.  
  
 Si cette clé de Registre n’est pas définie, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise la valeur par défaut de 0 pour les pilotes XPDM et de 4 pour les pilotes WDDM.  
  
<a name="requiredvideodriverdatesetting"></a>
## <a name="required-video-driver-date-setting"></a>Paramètre Date de pilote vidéo requise  
  
|Clé de Registre|Type de valeur|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|String|  
  
 En novembre 2004, Microsoft a publié une nouvelle version des lignes directrices sur les tests de conduite; les pilotes écrits après cette date offrent une meilleure stabilité. Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise le pipeline d’accélération matérielle pour ces pilotes et revient au rendu logiciel pour les pilotes XPDM publiés avant cette date.  
  
 Le **paramètre Date de pilote vidéo requise** vous permet de spécifier une autre date minimale pour les pilotes XPDM. Vous ne devez spécifier une date antérieure à novembre 2004 que si vous êtes sûr que votre pilote vidéo est assez stable pour prendre en charge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Le paramètre de pilote vidéo requis prend une chaîne au format suivant :  
  
| |  
|-|  
|*Yyyy* `/` *MM* `/` *DD*|  
  
 Où *AAAA* correspond l’année à quatre chiffres, *MM* correspond au mois à deux chiffres et *JJ* correspond au jour à deux chiffres. Lorsque cette valeur n’est pas définie, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise novembre 2004 comme date du pilote vidéo requis.  
  
<a name="usereferencerasterizeroption"></a>
## <a name="use-reference-rasterizer-option"></a>Option Utiliser le rastériseur de référence  
  
|Clé de Registre|Type de valeur|  
|------------------|----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 **L’option de rasterizer de référence d’utilisation** vous permet de forcer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dans un mode de rendu matériel simulé pour débogage: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] passe en mode matériel, mais utilise le logiciel de référence Microsoft Direct3D rasterizer, d3dref9.dll, au lieu d’un dispositif matériel réel.  
  
 Le rastériseur de référence est très lent, mais contourne votre pilote vidéo pour éviter tout problème de rendu provoqué par les problèmes liés au pilote. Pour cette raison, vous pouvez utiliser le rastériseur de référence pour déterminer si les problèmes de rendu sont provoqués par le pilote vidéo. Le fichier d3dref9.dll doit être dans un emplacement où l’application peut y accéder, comme n’importe quel emplacement dans le chemin d’accès système ou dans le répertoire local de l’application.  
  
 **L’option Utiliser le rastériseur de référence** prend une valeur DWORD. La valeur 0 indique que le rastériseur de référence n’est pas utilisé. Toute autre valeur non égale à 0 force [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à utiliser le rastériseur de référence.  
  
## <a name="see-also"></a>Voir aussi

- [Couches de rendu graphiques](../advanced/graphics-rendering-tiers.md)
- [Vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
