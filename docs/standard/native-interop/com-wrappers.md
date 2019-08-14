---
title: Wrappers COM
ms.date: 03/30/2017
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af9b87e83def5578ea38e94a4f69c657ac5f7c99
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631433"
---
# <a name="com-wrappers"></a><span data-ttu-id="3e160-102">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="3e160-102">COM Wrappers</span></span>
<span data-ttu-id="3e160-103">COM diffère du modèle objet de runtime .NET sur plusieurs points importants :</span><span class="sxs-lookup"><span data-stu-id="3e160-103">COM differs from the .NET runtime object model in several important ways:</span></span>  
  
- <span data-ttu-id="3e160-104">Les clients des objets COM doivent gérer la durée de vie de ces objets ; le common language runtime gère la durée de vie des objets dans son environnement.</span><span class="sxs-lookup"><span data-stu-id="3e160-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
- <span data-ttu-id="3e160-105">Les clients des objets COM déterminent si un service est disponible en demandant une interface qui fournit ce service et en récupérant le cas échéant un pointeur d’interface en retour.</span><span class="sxs-lookup"><span data-stu-id="3e160-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="3e160-106">Les clients des objets .NET peuvent obtenir une description de la fonctionnalité d’un objet par l’intermédiaire de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="3e160-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
- <span data-ttu-id="3e160-107">Les objets NET résident dans la mémoire managée par l’environnement d’exécution du runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="3e160-107">NET objects reside in memory managed by the .NET runtime execution environment.</span></span> <span data-ttu-id="3e160-108">Celui-ci peut déplacer des objets dans la mémoire en vue d’améliorer les performances et mettre à jour toutes les références aux objets qu’il déplace.</span><span class="sxs-lookup"><span data-stu-id="3e160-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="3e160-109">Les clients non managés, ayant obtenu un pointeur désignant un objet, s’attendent à ce que cet objet reste au même emplacement.</span><span class="sxs-lookup"><span data-stu-id="3e160-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="3e160-110">Ces clients ne disposent d’aucun mécanisme leur permettant d’utiliser un objet dont l’emplacement n’est pas fixe.</span><span class="sxs-lookup"><span data-stu-id="3e160-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="3e160-111">Pour surmonter ces différences, le runtime fournit des classes wrapper pour faire croire aux clients à la fois managés et non managés qu’ils appellent des objets dans leur environnement respectif.</span><span class="sxs-lookup"><span data-stu-id="3e160-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="3e160-112">Chaque fois que votre client managé appelle une méthode sur un objet COM, le runtime crée un [wrapper RCW (Runtime Callable Wrapper)](runtime-callable-wrapper.md).</span><span class="sxs-lookup"><span data-stu-id="3e160-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="3e160-113">Les wrappers RCW permettent, entre autres, de gommer les différences entre les mécanismes de référence managé et non managé.</span><span class="sxs-lookup"><span data-stu-id="3e160-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="3e160-114">Le runtime crée également un [wrapper CCW (COM Callable Wrapper)](com-callable-wrapper.md) pour inverser le processus, permettant ainsi à un client COM d’appeler de façon transparente une méthode sur un objet .NET.</span><span class="sxs-lookup"><span data-stu-id="3e160-114">The runtime also creates a [COM callable wrapper](com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="3e160-115">Ainsi que le montre l’illustration suivante, la perspective du code appelant détermine la classe wrapper créée par le runtime.</span><span class="sxs-lookup"><span data-stu-id="3e160-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 ![Vue d'ensemble du wrapper COM](./media/com-wrappers/bidirectional-com-overview.gif)  
  
 <span data-ttu-id="3e160-117">Dans la plupart des cas, les wrappers RCW ou CCW standard générés par le runtime assurent un marshaling adéquat pour les appels qui franchissent la limite séparant COM du runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="3e160-117">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET runtime.</span></span> <span data-ttu-id="3e160-118">En utilisant des attributs personnalisés, vous pouvez facultativement définir la façon dont le runtime représente le code managé et non managé.</span><span class="sxs-lookup"><span data-stu-id="3e160-118">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e160-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e160-119">See also</span></span>

- <span data-ttu-id="3e160-120">[Interopérabilité COM avancée dans .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3e160-120">[Advanced COM Interoperability in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="3e160-121">Wrapper pouvant être appelé par le runtime</span><span class="sxs-lookup"><span data-stu-id="3e160-121">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
- [<span data-ttu-id="3e160-122">Wrapper CCW (COM Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="3e160-122">COM Callable Wrapper</span></span>](com-callable-wrapper.md)
- <span data-ttu-id="3e160-123">[Personnalisation de wrappers standard dans .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3e160-123">[Customizing Standard Wrappers in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="3e160-124">[Guide pratique pour personnaliser des wrappers RCW dans .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3e160-124">[How to: Customize Runtime Callable Wrappers in .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/56kh4hy7(v=vs.100))</span></span>
