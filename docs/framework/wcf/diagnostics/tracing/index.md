---
title: Traçage
ms.date: 03/30/2017
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
ms.openlocfilehash: 569a97dc21a434cd711ad4c735f828df588f3af7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578979"
---
# <a name="tracing"></a><span data-ttu-id="cc4ad-102">Traçage</span><span class="sxs-lookup"><span data-stu-id="cc4ad-102">Tracing</span></span>
<span data-ttu-id="cc4ad-103">Windows Communication Foundation (WCF) fournit une instrumentation d’application et des données de diagnostic pour la surveillance et l’analyse des erreurs.</span><span class="sxs-lookup"><span data-stu-id="cc4ad-103">Windows Communication Foundation (WCF) provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="cc4ad-104">Vous pouvez utiliser le suivi au lieu d'un débogueur pour comprendre le comportement d'une application ou la raison de sa défaillance.</span><span class="sxs-lookup"><span data-stu-id="cc4ad-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="cc4ad-105">Vous pouvez également mettre en corrélation les erreurs et le traitement sur l'ensemble des composants afin de fournir une expérience de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="cc4ad-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 <span data-ttu-id="cc4ad-106">WCF génère les données suivantes pour le suivi de diagnostic :</span><span class="sxs-lookup"><span data-stu-id="cc4ad-106">WCF outputs the following data for diagnostic tracing:</span></span>  
  
- <span data-ttu-id="cc4ad-107">Suivis pour les jalons de processus sur l'ensemble des composants des applications, tels que les appels d'opération, exceptions de code, avertissements et autres événements de traitement significatifs.</span><span class="sxs-lookup"><span data-stu-id="cc4ad-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
- <span data-ttu-id="cc4ad-108">Événements d’erreur Windows en cas de dysfonctionnement de la fonctionnalité de suivi.</span><span class="sxs-lookup"><span data-stu-id="cc4ad-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc4ad-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="cc4ad-109">In This Section</span></span>  
 [<span data-ttu-id="cc4ad-110">Configuration du traçage</span><span class="sxs-lookup"><span data-stu-id="cc4ad-110">Configuring Tracing</span></span>](configuring-tracing.md)  
  
 <span data-ttu-id="cc4ad-111">Cette rubrique décrit comment configurer le suivi à différents niveaux en fonction de vos besoins spécifiques.</span><span class="sxs-lookup"><span data-stu-id="cc4ad-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="cc4ad-112">Suivi de bout en bout</span><span class="sxs-lookup"><span data-stu-id="cc4ad-112">End-to-End Tracing</span></span>](end-to-end-tracing.md)  
  
 <span data-ttu-id="cc4ad-113">Cette section décrit comment utiliser le suivi et la propagation d'activité pour la corrélation de bout en bout à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="cc4ad-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="cc4ad-114">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="cc4ad-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="cc4ad-115">Cette section décrit comment utiliser le suivi pour déboguer votre application.</span><span class="sxs-lookup"><span data-stu-id="cc4ad-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="cc4ad-116">Problèmes de sécurité et conseils utiles pour le suivi</span><span class="sxs-lookup"><span data-stu-id="cc4ad-116">Security Concerns and Useful Tips for Tracing</span></span>](security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="cc4ad-117">Cette rubrique décrit comment empêcher l'exposition des informations sensibles et fournit également des conseils utiles en cas d'utilisation de WebHost.</span><span class="sxs-lookup"><span data-stu-id="cc4ad-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="cc4ad-118">Référence des suivis</span><span class="sxs-lookup"><span data-stu-id="cc4ad-118">Traces Reference</span></span>](traces-reference.md)  
  
 <span data-ttu-id="cc4ad-119">Cette rubrique répertorie tous les suivis générés par WCF.</span><span class="sxs-lookup"><span data-stu-id="cc4ad-119">This topic lists all the traces generated by WCF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc4ad-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc4ad-120">See also</span></span>

- [<span data-ttu-id="cc4ad-121">Outil Service Trace Viewer (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="cc4ad-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
