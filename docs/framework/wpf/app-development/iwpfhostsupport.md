---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: e3edd7f7080562d03453898dba7a9326561803b5
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124193"
---
# <a name="iwpfhostsupport"></a><span data-ttu-id="c15a7-102">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="c15a7-102">IWpfHostSupport</span></span>
<span data-ttu-id="c15a7-103">Les applications qui hébergent [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] contenu via PresentationHost. exe implémentent cette interface pour fournir un point d’intégration entre l’hôte et PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="c15a7-103">Applications that host [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content via PresentationHost.exe implement this interface to provide a point of integration between the host and PresentationHost.exe.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c15a7-104">Notes</span><span class="sxs-lookup"><span data-stu-id="c15a7-104">Remarks</span></span>  
 <span data-ttu-id="c15a7-105">Les applications Win32, telles que les navigateurs Web, peuvent héberger du contenu WPF, y compris des applications de navigateur XAML (XBAP) et du code XAML libre.</span><span class="sxs-lookup"><span data-stu-id="c15a7-105">Win32 applications such as Web browsers can host WPF content, including XAML browser applications (XBAPs) and loose XAML.</span></span> <span data-ttu-id="c15a7-106">Pour héberger du contenu WPF, les applications Win32 créent une instance du [contrôle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="c15a7-106">To host WPF content, Win32 applications create an instance of the [WebBrowser control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span></span> <span data-ttu-id="c15a7-107">Pour être hébergé, WPF crée une instance de PresentationHost. exe, qui fournit le contenu WPF hébergé à l’hôte en vue de son affichage dans le [contrôle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="c15a7-107">To be hosted, WPF creates an instance of PresentationHost.exe, which provides the hosted WPF content to the host for display in the [WebBrowser control](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).</span></span>  
  
 <span data-ttu-id="c15a7-108">L’intégration activée par `IWpfHostSupport` permet à PresentationHost. exe d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="c15a7-108">The integration enabled by `IWpfHostSupport` allows PresentationHost.exe to:</span></span>  
  
- <span data-ttu-id="c15a7-109">Détectez et inscrivez-vous auprès des périphériques d’entrée bruts (périphériques d’interface utilisateur) qui intéressent l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="c15a7-109">Discover and register with the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>  
  
- <span data-ttu-id="c15a7-110">Recevoir des messages d’entrée des périphériques d’entrée bruts inscrits et transférer les messages appropriés à l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="c15a7-110">Receive input messages from the registered raw input devices and forward appropriate messages to the host application.</span></span>  
  
- <span data-ttu-id="c15a7-111">Interrogez l’application hôte pour obtenir des interfaces utilisateur de progression et d’erreur personnalisées.</span><span class="sxs-lookup"><span data-stu-id="c15a7-111">Query the host application for custom progress and error user interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c15a7-112">Cette API est conçue et pris en charge uniquement sur l'ordinateur client local</span><span class="sxs-lookup"><span data-stu-id="c15a7-112">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="c15a7-113">Membres</span><span class="sxs-lookup"><span data-stu-id="c15a7-113">Members</span></span>  
  
|<span data-ttu-id="c15a7-114">Membre</span><span class="sxs-lookup"><span data-stu-id="c15a7-114">Member</span></span>|<span data-ttu-id="c15a7-115">Description</span><span class="sxs-lookup"><span data-stu-id="c15a7-115">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c15a7-116">GetRawInputDevices</span><span class="sxs-lookup"><span data-stu-id="c15a7-116">GetRawInputDevices</span></span>](getrawinputdevices.md)|<span data-ttu-id="c15a7-117">Permet à PresentationHost.exe de découvrir les périphériques d'entrée brute (périphériques d'interface utilisateur) qui intéressent l'application hôte.</span><span class="sxs-lookup"><span data-stu-id="c15a7-117">Allows PresentationHost.exe to discover the raw input devices (Human Interface Devices) that the host application is interested in.</span></span>|  
|[<span data-ttu-id="c15a7-118">FilterInputMessage</span><span class="sxs-lookup"><span data-stu-id="c15a7-118">FilterInputMessage</span></span>](filterinputmessage.md)|<span data-ttu-id="c15a7-119">Appelé par PresentationHost.exe chaque fois qu'un message est reçu, à moins que E_NOTIMPL soit retourné.</span><span class="sxs-lookup"><span data-stu-id="c15a7-119">Called by PresentationHost.exe whenever a message is received unless E_NOTIMPL is returned.</span></span>|  
|[<span data-ttu-id="c15a7-120">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="c15a7-120">GetCustomUI</span></span>](getcustomui.md)|<span data-ttu-id="c15a7-121">Par défaut, PresentationHost. exe fournit ses propres paramètres de progression et d’erreur de déploiement qui sont affichés lorsque le contenu WPF est déployé.</span><span class="sxs-lookup"><span data-stu-id="c15a7-121">By default, PresentationHost.exe provides its own deployment progress and deployment error user interfaces that are displayed when WPF content is deployed.</span></span>|
