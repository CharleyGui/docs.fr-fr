---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 97a120c57624ada32e6661bd8a613c4ea1d01b2f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591387"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="00cfb-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="00cfb-102">IWpfHostSupport</span></span>
<span data-ttu-id="00cfb-103">Les applications qui hébergent [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] contenu via PresentationHost.exe implémentent cette interface pour fournir un point d’intégration entre l’hôte et PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="00cfb-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00cfb-104">Notes</span><span class="sxs-lookup"><span data-stu-id="00cfb-104">Remarks</span></span>  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] <span data-ttu-id="00cfb-105">applications telles que les navigateurs Web peuvent héberger [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] de contenu, y compris [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] et libre de XAML.</span><span class="sxs-lookup"><span data-stu-id="00cfb-105">applications such as Web browsers can host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, including [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] and loose XAML.</span></span> <span data-ttu-id="00cfb-106">À l’hôte [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] contenu, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications créent une instance de la [contrôle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="00cfb-106">To host [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications create an instance of the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span> <span data-ttu-id="00cfb-107">Doit être hébergé, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] crée une instance de PresentationHost.exe, qui fournit le texte hébergé [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] contenu à l’hôte pour l’affichage dans le [contrôle WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).</span><span class="sxs-lookup"><span data-stu-id="00cfb-107">To be hosted, [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] creates an instance of PresentationHost.exe, which provides the hosted [!INCLUDE[TLA#tla_titlewinclient](../../../../includes/tlasharptla-titlewinclient-md.md)] content to the host for display in the [WebBrowser control](https://go.microsoft.com/fwlink/?LinkId=97911).</span></span>  
  
 <span data-ttu-id="00cfb-108">L’intégration activée par `IWpfHostSupport` permet à PresentationHost.exe de :</span><span class="sxs-lookup"><span data-stu-id="00cfb-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="00cfb-109">Découvrir et enregistrer avec les périphériques d’entrée brute (périphériques d’Interface utilisateur) qui intéresse l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="00cfb-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="00cfb-110">Recevoir des messages d’entrée à partir des périphériques d’entrée brute et transférer les messages appropriés à l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="00cfb-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="00cfb-111">L’application hôte pour les interfaces d’utilisateur de progression et d’erreur personnalisées de la requête.</span><span class="sxs-lookup"><span data-stu-id="00cfb-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00cfb-112">Cette API est conçue et pris en charge uniquement sur l'ordinateur client local</span><span class="sxs-lookup"><span data-stu-id="00cfb-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="00cfb-113">Membres</span><span class="sxs-lookup"><span data-stu-id="00cfb-113">Members</span></span>  
  
|<span data-ttu-id="00cfb-114">Membre</span><span class="sxs-lookup"><span data-stu-id="00cfb-114">Member</span></span>|<span data-ttu-id="00cfb-115">Description</span><span class="sxs-lookup"><span data-stu-id="00cfb-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00cfb-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="00cfb-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="00cfb-117">Permet à PresentationHost.exe de découvrir les périphériques d'entrée brute (périphériques d'interface utilisateur) qui intéressent l'application hôte.</span><span class="sxs-lookup"><span data-stu-id="00cfb-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="00cfb-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="00cfb-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="00cfb-119">Appelé par PresentationHost.exe chaque fois qu'un message est reçu, à moins que E_NOTIMPL soit retourné.</span><span class="sxs-lookup"><span data-stu-id="00cfb-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="00cfb-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="00cfb-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="00cfb-121">Par défaut, PresentationHost.exe fournit sa propre progression du déploiement et une erreur de déploiement des interfaces utilisateur qui sont affichent lorsque le contenu WPF est déployé.</span><span class="sxs-lookup"><span data-stu-id="00cfb-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
