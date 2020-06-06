---
title: Exceptions du runtime dans les applications natives .NET
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
ms.openlocfilehash: 12df2ef7bf6e86a60dfa4c130f35969e72ac5211
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180952"
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="8c393-102">Exceptions du runtime dans les applications natives .NET</span><span class="sxs-lookup"><span data-stu-id="8c393-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="8c393-103">Il est important de tester les versions release de votre application de plateforme Windows universelle sur leurs plateformes cibles, car les configurations debug et release sont totalement différentes.</span><span class="sxs-lookup"><span data-stu-id="8c393-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="8c393-104">Par défaut, la configuration debug utilise le runtime .NET Core pour compiler votre application, mais la configuration release utilise .NET Native pour compiler votre application en code natif.</span><span class="sxs-lookup"><span data-stu-id="8c393-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8c393-105">Pour plus d’informations sur la gestion des exceptions [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)et [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) que vous pouvez rencontrer lors du test des versions release de votre application, consultez la section «étape 4 : résoudre manuellement les métadonnées manquantes : dans la rubrique [prise en main](getting-started-with-net-native.md) , ainsi que la référence de fichier de configuration de la [réflexion et](reflection-and-net-native.md) de la .net native et des [directives Runtime (Rd. Xml)](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="8c393-105">For information on dealing with the [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see "Step 4: Manually resolve missing metadata: in the [Getting Started](getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="8c393-106">Versions debug et release</span><span class="sxs-lookup"><span data-stu-id="8c393-106">Debug and release builds</span></span>  
 <span data-ttu-id="8c393-107">Quand la version debug s’exécute sur le runtime .NET Core, elle n’a pas été compilée en code natif.</span><span class="sxs-lookup"><span data-stu-id="8c393-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="8c393-108">Ainsi, tous les services normalement fournis par le runtime sont accessibles à votre application.</span><span class="sxs-lookup"><span data-stu-id="8c393-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="8c393-109">D’autre part, la version release est compilée en code natif pour ses plateformes cibles, elle supprime la plupart des dépendances vis-à-vis des runtimes et bibliothèques externes et elle optimise largement le code à des fins de performances maximales.</span><span class="sxs-lookup"><span data-stu-id="8c393-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="8c393-110">Quand vous déboguez des versions release qui sont compilées à l’aide de .NET Native :</span><span class="sxs-lookup"><span data-stu-id="8c393-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
- <span data-ttu-id="8c393-111">Vous utilisez le moteur de débogage .NET Native, qui est différent des outils de débogage .NET normaux.</span><span class="sxs-lookup"><span data-stu-id="8c393-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
- <span data-ttu-id="8c393-112">La taille de votre fichier exécutable est réduite autant que possible.</span><span class="sxs-lookup"><span data-stu-id="8c393-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="8c393-113">L’une des façons employées par .NET Native pour réduire la taille d’un fichier exécutable est en filtrant considérablement les messages d’exception d’exécution, un sujet abordé de façon plus détaillée dans la section [Runtime exception messages](#Messages) .</span><span class="sxs-lookup"><span data-stu-id="8c393-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
- <span data-ttu-id="8c393-114">Votre code est largement optimisé.</span><span class="sxs-lookup"><span data-stu-id="8c393-114">Your code is heavily optimized.</span></span> <span data-ttu-id="8c393-115">Cela signifie que cette incorporation est utilisée dès que possible.</span><span class="sxs-lookup"><span data-stu-id="8c393-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="8c393-116">(L’incorporation déplace le code des routines externes dans la routine d’appel.)   Le fait que .NET Native fournit un Runtime spécialisé et implémente une incorporation agressive affecte la pile des appels qui s’affiche lors du débogage.</span><span class="sxs-lookup"><span data-stu-id="8c393-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="8c393-117">Pour plus d’informations, consultez la section [Runtime call stack](#CallStack) .</span><span class="sxs-lookup"><span data-stu-id="8c393-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c393-118">Vous pouvez déterminer si les versions debug et release sont compilées avec la chaîne d’outils .NET Native en cochant ou non la case **Compiler avec la chaîne de l’outil du code natif .NET** .</span><span class="sxs-lookup"><span data-stu-id="8c393-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="8c393-119">Notez quand même que le Windows Store compile toujours la version de production de votre application avec la chaîne d’outils .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8c393-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>
## <a name="runtime-exception-messages"></a><span data-ttu-id="8c393-120">Runtime exception messages</span><span class="sxs-lookup"><span data-stu-id="8c393-120">Runtime exception messages</span></span>  
 <span data-ttu-id="8c393-121">Pour réduire la taille de l’exécutable de l’application, .NET Native n’inclut pas le texte complet des messages d’exception.</span><span class="sxs-lookup"><span data-stu-id="8c393-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="8c393-122">Ainsi, les exceptions du runtime levées dans les versions release risquent de ne pas afficher le texte complet des messages d’exception.</span><span class="sxs-lookup"><span data-stu-id="8c393-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="8c393-123">Le texte peut plutôt consister en une sous-chaîne assortie d’un lien à suivre pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="8c393-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="8c393-124">Par exemple, les informations sur l’exception peuvent apparaître comme suit :</span><span class="sxs-lookup"><span data-stu-id="8c393-124">For example, the exception information may appear as:</span></span>  
  
```output
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="8c393-125">Si vous avez besoin de consulter la totalité du message d’exception, exécutez plutôt la version debug.</span><span class="sxs-lookup"><span data-stu-id="8c393-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="8c393-126">Par exemple, les informations sur l’exception précédente issues de la version release peuvent apparaître comme suit dans la version debug :</span><span class="sxs-lookup"><span data-stu-id="8c393-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```output
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>
## <a name="runtime-call-stack"></a><span data-ttu-id="8c393-127">Runtime call stack</span><span class="sxs-lookup"><span data-stu-id="8c393-127">Runtime call stack</span></span>  
 <span data-ttu-id="8c393-128">Du fait de l’incorporation et des autres optimisations, la pile des appels affichée par une application compilée par la chaîne d’outils .NET Native risque de ne pas vous aider à identifier clairement le chemin vers une exception runtime.</span><span class="sxs-lookup"><span data-stu-id="8c393-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="8c393-129">Pour obtenir la pile complète, exécutez plutôt la version debug.</span><span class="sxs-lookup"><span data-stu-id="8c393-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c393-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c393-130">See also</span></span>

- [<span data-ttu-id="8c393-131">Débogage des applications Windows universelles .NET Native</span><span class="sxs-lookup"><span data-stu-id="8c393-131">Debugging .NET Native Windows Universal Apps</span></span>](https://devblogs.microsoft.com/devops/debugging-net-native-windows-universal-apps/)
- [<span data-ttu-id="8c393-132">Prise en main</span><span class="sxs-lookup"><span data-stu-id="8c393-132">Getting Started</span></span>](getting-started-with-net-native.md)
