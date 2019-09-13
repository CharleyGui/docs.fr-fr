---
title: Exceptions du runtime dans les applications natives .NET
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68fe50d24ce547e1cad092e3d871c2d0990fd5af
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894980"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="edc66-102">Exceptions du runtime dans les applications natives .NET</span><span class="sxs-lookup"><span data-stu-id="edc66-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="edc66-103">Il est important de tester les versions release de votre application de plateforme Windows universelle sur leurs plateformes cibles, car les configurations debug et release sont totalement différentes.</span><span class="sxs-lookup"><span data-stu-id="edc66-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="edc66-104">Par défaut, la configuration debug utilise le runtime .NET Core pour compiler votre application, mais la configuration release utilise .NET Native pour compiler votre application en code natif.</span><span class="sxs-lookup"><span data-stu-id="edc66-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="edc66-105">Pour plus d’informations sur la gestion des exceptions [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)et [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) que vous pouvez rencontrer lors du test des versions release de votre application, consultez la section «étape 4 : Résoudre manuellement les métadonnées manquantes : dans la rubrique [prise en main](../../../docs/framework/net-native/getting-started-with-net-native.md) , ainsi que la référence du fichier de configuration de la [réflexion et des .net Native](../../../docs/framework/net-native/reflection-and-net-native.md) et des [directives Runtime (Rd. Xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="edc66-105">For information on dealing with the [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see  "Step 4: Manually resolve missing metadata: in the [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="edc66-106">Versions debug et release</span><span class="sxs-lookup"><span data-stu-id="edc66-106">Debug and release builds</span></span>  
 <span data-ttu-id="edc66-107">Quand la version debug s’exécute sur le runtime .NET Core, elle n’a pas été compilée en code natif.</span><span class="sxs-lookup"><span data-stu-id="edc66-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="edc66-108">Ainsi, tous les services normalement fournis par le runtime sont accessibles à votre application.</span><span class="sxs-lookup"><span data-stu-id="edc66-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="edc66-109">D’autre part, la version release est compilée en code natif pour ses plateformes cibles, elle supprime la plupart des dépendances vis-à-vis des runtimes et bibliothèques externes et elle optimise largement le code à des fins de performances maximales.</span><span class="sxs-lookup"><span data-stu-id="edc66-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="edc66-110">Quand vous déboguez des versions release qui sont compilées à l’aide de .NET Native :</span><span class="sxs-lookup"><span data-stu-id="edc66-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
- <span data-ttu-id="edc66-111">Vous utilisez le moteur de débogage .NET Native, qui est différent des outils de débogage .NET normaux.</span><span class="sxs-lookup"><span data-stu-id="edc66-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
- <span data-ttu-id="edc66-112">La taille de votre fichier exécutable est réduite autant que possible.</span><span class="sxs-lookup"><span data-stu-id="edc66-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="edc66-113">L’une des façons employées par .NET Native pour réduire la taille d’un fichier exécutable est en filtrant considérablement les messages d’exception d’exécution, un sujet abordé de façon plus détaillée dans la section [Runtime exception messages](#Messages) .</span><span class="sxs-lookup"><span data-stu-id="edc66-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
- <span data-ttu-id="edc66-114">Votre code est largement optimisé.</span><span class="sxs-lookup"><span data-stu-id="edc66-114">Your code is heavily optimized.</span></span> <span data-ttu-id="edc66-115">Cela signifie que cette incorporation est utilisée dès que possible.</span><span class="sxs-lookup"><span data-stu-id="edc66-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="edc66-116">(L’incorporation déplace le code depuis les routines externes vers la routine d’appel.)   Le fait que .NET Native fournisse un runtime spécialisé et implémente une incorporation agressive affecte la pile des appels qui s’affiche lors du débogage.</span><span class="sxs-lookup"><span data-stu-id="edc66-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="edc66-117">Pour plus d’informations, consultez la section [Runtime call stack](#CallStack) .</span><span class="sxs-lookup"><span data-stu-id="edc66-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edc66-118">Vous pouvez déterminer si les versions debug et release sont compilées avec la chaîne d’outils .NET Native en cochant ou non la case **Compiler avec la chaîne de l’outil du code natif .NET** .</span><span class="sxs-lookup"><span data-stu-id="edc66-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="edc66-119">Notez quand même que le Windows Store compile toujours la version de production de votre application avec la chaîne d’outils .NET Native.</span><span class="sxs-lookup"><span data-stu-id="edc66-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a><span data-ttu-id="edc66-120">Runtime exception messages</span><span class="sxs-lookup"><span data-stu-id="edc66-120">Runtime exception messages</span></span>  
 <span data-ttu-id="edc66-121">Pour réduire la taille de l’exécutable de l’application, .NET Native n’inclut pas le texte complet des messages d’exception.</span><span class="sxs-lookup"><span data-stu-id="edc66-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="edc66-122">Ainsi, les exceptions du runtime levées dans les versions release risquent de ne pas afficher le texte complet des messages d’exception.</span><span class="sxs-lookup"><span data-stu-id="edc66-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="edc66-123">Le texte peut plutôt consister en une sous-chaîne assortie d’un lien à suivre pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="edc66-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="edc66-124">Par exemple, les informations sur l’exception peuvent apparaître comme suit :</span><span class="sxs-lookup"><span data-stu-id="edc66-124">For example, the exception information may appear as:</span></span>  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="edc66-125">Si vous avez besoin de consulter la totalité du message d’exception, exécutez plutôt la version debug.</span><span class="sxs-lookup"><span data-stu-id="edc66-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="edc66-126">Par exemple, les informations sur l’exception précédente issues de la version release peuvent apparaître comme suit dans la version debug :</span><span class="sxs-lookup"><span data-stu-id="edc66-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a><span data-ttu-id="edc66-127">Runtime call stack</span><span class="sxs-lookup"><span data-stu-id="edc66-127">Runtime call stack</span></span>  
 <span data-ttu-id="edc66-128">Du fait de l’incorporation et des autres optimisations, la pile des appels affichée par une application compilée par la chaîne d’outils .NET Native risque de ne pas vous aider à identifier clairement le chemin vers une exception runtime.</span><span class="sxs-lookup"><span data-stu-id="edc66-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="edc66-129">Pour obtenir la pile complète, exécutez plutôt la version debug.</span><span class="sxs-lookup"><span data-stu-id="edc66-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edc66-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edc66-130">See also</span></span>

- [<span data-ttu-id="edc66-131">Débogage .NET Native des applications universelles Windows</span><span class="sxs-lookup"><span data-stu-id="edc66-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="edc66-132">Prise en main</span><span class="sxs-lookup"><span data-stu-id="edc66-132">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
