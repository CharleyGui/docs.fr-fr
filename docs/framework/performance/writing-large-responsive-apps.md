---
title: Conception d'applications .NET Framework complexes et réactives
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 57f65feff5260cb83df5354f5d7ee1bad0babb3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180583"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="a5f62-102">Conception d'applications .NET Framework complexes et réactives</span><span class="sxs-lookup"><span data-stu-id="a5f62-102">Writing Large, Responsive .NET Framework Apps</span></span>

<span data-ttu-id="a5f62-103">Cet article fournit des conseils pour améliorer les performances d'applications .NET Framework volumineuses ou d'applications qui traitent de grandes quantités de données, telles que des fichiers ou des bases de données.</span><span class="sxs-lookup"><span data-stu-id="a5f62-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="a5f62-104">Ces conseils proviennent de la réécriture des compilateurs C# et Visual Basic en code managé, et cet article inclut plusieurs exemples réels issus du compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="a5f62-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span>
  
<span data-ttu-id="a5f62-105">Le .NET Framework est hautement productif pour la création d'applications.</span><span class="sxs-lookup"><span data-stu-id="a5f62-105">The .NET Framework is highly productive for building apps.</span></span> <span data-ttu-id="a5f62-106">Des langages puissants et sécurisés, ainsi qu’une riche collection de bibliothèques, favorisent une création d’applications très fructueuse.</span><span class="sxs-lookup"><span data-stu-id="a5f62-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span> <span data-ttu-id="a5f62-107">Toutefois, une grande productivité implique des responsabilités.</span><span class="sxs-lookup"><span data-stu-id="a5f62-107">However, with great productivity comes responsibility.</span></span> <span data-ttu-id="a5f62-108">Vous devez utiliser toute la puissance du .NET Framework, mais vous devez être prêt à régler les performances de votre code lorsque cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="a5f62-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span>
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="a5f62-109">Raisons pour lesquelles les performances des nouveaux compilateurs s'appliquent à votre application</span><span class="sxs-lookup"><span data-stu-id="a5f62-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="a5f62-110">L'équipe chargée de la plateforme des compilateurs .NET (« Roslyn ») a réécrit les compilateurs C# et Visual Basic en code managé pour fournir de nouvelles API afin de modéliser et analyser le code, de créer des outils et de favoriser des expériences de programmation nettement plus riches dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5f62-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span> <span data-ttu-id="a5f62-111">La réécriture des compilateurs et la création d'expériences Visual Studio sur les nouveaux compilateurs ont été source de riches enseignements en matière de performances, qui sont transposables à toute application .NET Framework volumineuse et à toute application qui traite une grande quantité de données.</span><span class="sxs-lookup"><span data-stu-id="a5f62-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span> <span data-ttu-id="a5f62-112">Vous n'avez pas besoin de connaître les compilateurs pour tirer profit des enseignements et des exemples issus du compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="a5f62-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span>
  
 <span data-ttu-id="a5f62-113">Visual Studio utilise les API de compilateur pour générer toutes les fonctionnalités IntelliSense tant appréciées des utilisateurs, telles que la colorisation des identificateurs et des mots clés, les listes de saisie semi-automatique de syntaxe, les tildes d’erreur, les paramètres conseillés, les problèmes de code et les actions de code.</span><span class="sxs-lookup"><span data-stu-id="a5f62-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span> <span data-ttu-id="a5f62-114">Visual Studio fournit cette aide pendant que les développeurs saisissent et modifient leur code, et Visual Studio doit rester réactif pendant que le compilateur modélise de façon continue le code que les développeurs modifient.</span><span class="sxs-lookup"><span data-stu-id="a5f62-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span>
  
 <span data-ttu-id="a5f62-115">Quand vos utilisateurs finaux interagissent avec votre application, ils attendent d'elle qu'elle soit réactive.</span><span class="sxs-lookup"><span data-stu-id="a5f62-115">When your end users interact with your app, they expect it to be responsive.</span></span> <span data-ttu-id="a5f62-116">La saisie ou la gestion des commandes ne doivent jamais être bloquées.</span><span class="sxs-lookup"><span data-stu-id="a5f62-116">Typing or command handling should never be blocked.</span></span> <span data-ttu-id="a5f62-117">De l'aide doit s'afficher rapidement ou disparaître si l'utilisateur poursuit la saisie.</span><span class="sxs-lookup"><span data-stu-id="a5f62-117">Help should pop up quickly or give up if the user continues typing.</span></span> <span data-ttu-id="a5f62-118">Votre application doit éviter de bloquer le thread d'interface utilisateur avec de longs calculs qui donnent l'impression que l'application ne réagit pas.</span><span class="sxs-lookup"><span data-stu-id="a5f62-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span>
  
 <span data-ttu-id="a5f62-119">Pour plus d’informations sur les compilateurs Roslyn, voir [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span><span class="sxs-lookup"><span data-stu-id="a5f62-119">For more information about Roslyn compilers, see [The .NET Compiler Platform SDK](../../csharp/roslyn-sdk/index.md).</span></span>
  
## <a name="just-the-facts"></a><span data-ttu-id="a5f62-120">Les faits</span><span class="sxs-lookup"><span data-stu-id="a5f62-120">Just the Facts</span></span>  
 <span data-ttu-id="a5f62-121">Prenez en compte les faits suivants lorsque vous réglez les performances de vos applications .NET Framework pour les rendre plus réactives.</span><span class="sxs-lookup"><span data-stu-id="a5f62-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span>
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="a5f62-122">Fait n° 1 : N'optimisez pas prématurément</span><span class="sxs-lookup"><span data-stu-id="a5f62-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="a5f62-123">L'écriture d'un code plus complexe que nécessaire entraîne des coûts de maintenance, de débogage et de finition.</span><span class="sxs-lookup"><span data-stu-id="a5f62-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span> <span data-ttu-id="a5f62-124">Les programmeurs expérimentés ont une compréhension intuitive de la manière de résoudre les problèmes de codage et écrivent des codes plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="a5f62-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span> <span data-ttu-id="a5f62-125">Toutefois, ils optimisent parfois prématurément leur code.</span><span class="sxs-lookup"><span data-stu-id="a5f62-125">However, they sometimes prematurely optimize their code.</span></span> <span data-ttu-id="a5f62-126">Par exemple, ils utilisent une table de hachage lorsqu'un simple tableau suffirait, ou ils utilisent une mise en cache compliquée susceptible d'engendrer des fuites de mémoire au lieu de simplement recalculer les valeurs.</span><span class="sxs-lookup"><span data-stu-id="a5f62-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span> <span data-ttu-id="a5f62-127">Même si vous êtes un programmeur expérimenté, vous devez tester les performances et analyser votre code quand vous décelez des problèmes.</span><span class="sxs-lookup"><span data-stu-id="a5f62-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span>
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="a5f62-128">Fait n° 2 : Si vous n'effectuez pas de mesures, vous ne faites que supposer</span><span class="sxs-lookup"><span data-stu-id="a5f62-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="a5f62-129">Les profils et les mesures ne trompent pas.</span><span class="sxs-lookup"><span data-stu-id="a5f62-129">Profiles and measurements don’t lie.</span></span> <span data-ttu-id="a5f62-130">Les profils vous montrent si l'UC est pleinement chargée ou si vous êtes bloqué au niveau des E/S de disque.</span><span class="sxs-lookup"><span data-stu-id="a5f62-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span> <span data-ttu-id="a5f62-131">Les profils indiquent le type et la quantité de mémoire que vous allouez et si le processus [garbage collection](../../standard/garbage-collection/index.md) (GC) utilise beaucoup de ressources de votre UC.</span><span class="sxs-lookup"><span data-stu-id="a5f62-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../standard/garbage-collection/index.md) (GC).</span></span>
  
 <span data-ttu-id="a5f62-132">Vous devez définir des objectifs de performances pour des scénarios ou des expériences clients clés dans votre application, et écrire des tests pour mesurer les performances.</span><span class="sxs-lookup"><span data-stu-id="a5f62-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span> <span data-ttu-id="a5f62-133">Étudiez les échecs des tests en appliquant un raisonnement scientifique : utilisez des profils pour vous guider, avancez des hypothèses concernant la nature du problème et testez vos hypothèses en faisant des expériences ou en apportant des modifications au code.</span><span class="sxs-lookup"><span data-stu-id="a5f62-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span> <span data-ttu-id="a5f62-134">Établissez des mesures de performances de planning de référence au fil du temps en effectuant des tests réguliers, afin de pouvoir isoler les changements qui provoquent des régressions des performances.</span><span class="sxs-lookup"><span data-stu-id="a5f62-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span> <span data-ttu-id="a5f62-135">Grâce à une approche rigoureuse du traitement des performances, vous éviterez de perdre du temps avec des mises à jour de code inutiles.</span><span class="sxs-lookup"><span data-stu-id="a5f62-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span>
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="a5f62-136">Fait n° 3 : Des outils efficaces font toute la différence</span><span class="sxs-lookup"><span data-stu-id="a5f62-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="a5f62-137">Des outils efficaces vous permettent de plonger directement au cœur des principaux problèmes de performances (UC, mémoire ou disque) et vous aident à localiser le code à l'origine des goulots d'étranglement.</span><span class="sxs-lookup"><span data-stu-id="a5f62-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span> <span data-ttu-id="a5f62-138">Microsoft expédie une variété d’outils de performance tels que [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) et [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span><span class="sxs-lookup"><span data-stu-id="a5f62-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling) and [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).</span></span>
  
 <span data-ttu-id="a5f62-139">PerfView est un outil gratuit et extrêmement puissant qui vous permet de porter toute votre attention sur des problèmes profonds liés par exemple aux E/S de disque, aux événements du GC et à la mémoire.</span><span class="sxs-lookup"><span data-stu-id="a5f62-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span> <span data-ttu-id="a5f62-140">Vous pouvez capturer des événements de [suivi d’événements pour Windows](../wcf/samples/etw-tracing.md) (ETW) liés aux performances et afficher aisément les informations pour chaque application, processus, pile et thread.</span><span class="sxs-lookup"><span data-stu-id="a5f62-140">You can capture performance-related [Event Tracing for Windows](../wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span> <span data-ttu-id="a5f62-141">PerfView vous montre la quantité et le type de mémoire que votre application alloue, ainsi que les fonctions ou les piles d'appels qui contribuent aux allocations de mémoire, et pour quels volumes.</span><span class="sxs-lookup"><span data-stu-id="a5f62-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="a5f62-142">Pour plus de détails, consultez l’ensemble complet de rubriques d’aide, de démonstrations et de vidéos fournies avec l’outil (par exemple, les [didacticiels PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) sur Channel 9).</span><span class="sxs-lookup"><span data-stu-id="a5f62-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](https://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span>
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="a5f62-143">Fait n° 4 : Tout se résume aux allocations</span><span class="sxs-lookup"><span data-stu-id="a5f62-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="a5f62-144">Vous pouvez penser que la création d'une application .NET Framework réactive n'est qu'une question d'algorithmes, comme l'utilisation d'un tri rapide à la place d'un tri par propagation, mais ce n'est pas le cas.</span><span class="sxs-lookup"><span data-stu-id="a5f62-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span> <span data-ttu-id="a5f62-145">Le facteur principal qui intervient dans la création d'une application réactive et l'allocation de la mémoire, notamment quand votre application est très volumineuse ou traite de grandes quantités de données.</span><span class="sxs-lookup"><span data-stu-id="a5f62-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span>
  
 <span data-ttu-id="a5f62-146">Quasiment tout le travail nécessaire pour créer des expériences IDE réactives avec les API des nouveaux compilateurs a impliqué d’éviter les allocations et de gérer les stratégies de mise en cache.</span><span class="sxs-lookup"><span data-stu-id="a5f62-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span> <span data-ttu-id="a5f62-147">Les traces PerfView indiquent que les performances des nouveaux compilateurs C# et Visual Basic sont rarement liées à l'UC.</span><span class="sxs-lookup"><span data-stu-id="a5f62-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span> <span data-ttu-id="a5f62-148">Les compilateurs peuvent être liés aux E/S lors de la lecture de centaines de milliers ou de millions de lignes de code, lors de la lecture des métadonnées ou lors de l'émission du code généré.</span><span class="sxs-lookup"><span data-stu-id="a5f62-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span> <span data-ttu-id="a5f62-149">Les retards de threads d’interface utilisateur sont quasiment tous dus au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a5f62-149">The UI thread delays are nearly all due to garbage collection.</span></span> <span data-ttu-id="a5f62-150">Le GC du .NET Framework fait l'objet d'un réglage précis pour les performances et effectue une grande part de son travail pendant que le code de l'application s'exécute.</span><span class="sxs-lookup"><span data-stu-id="a5f62-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span> <span data-ttu-id="a5f62-151">Toutefois, une seule allocation peut déclencher une collection [gen2](../../standard/garbage-collection/fundamentals.md) coûteuse, susceptible d’arrêter tous les threads.</span><span class="sxs-lookup"><span data-stu-id="a5f62-151">However, a single allocation can trigger an expensive [gen2](../../standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span>
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="a5f62-152">Allocations courantes et exemples courants</span><span class="sxs-lookup"><span data-stu-id="a5f62-152">Common allocations and examples</span></span>  
 <span data-ttu-id="a5f62-153">Les exemples d'expressions fournis dans cette section possèdent des allocations masquées qui apparaissent réduites.</span><span class="sxs-lookup"><span data-stu-id="a5f62-153">The example expressions in this section have hidden allocations that appear small.</span></span> <span data-ttu-id="a5f62-154">Toutefois, si une application volumineuse exécute ces expressions suffisamment de fois, elles peuvent entraîner l'allocation de centaines de méga-octets, voire même de plusieurs giga-octets, de mémoire.</span><span class="sxs-lookup"><span data-stu-id="a5f62-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span> <span data-ttu-id="a5f62-155">Par exemple, des tests d'une minute simulant une phase de saisie par un développeur dans l'éditeur ont alloué plusieurs giga-octets de mémoire et conduit l'équipe de performances à se concentrer sur des scénarios de saisie.</span><span class="sxs-lookup"><span data-stu-id="a5f62-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span>
  
### <a name="boxing"></a><span data-ttu-id="a5f62-156">Boxing</span><span class="sxs-lookup"><span data-stu-id="a5f62-156">Boxing</span></span>  
 <span data-ttu-id="a5f62-157">Le [boxing](../../csharp/programming-guide/types/boxing-and-unboxing.md) intervient quand des types valeur situés normalement sur la pile ou dans des structures de données sont encapsulés dans un objet.</span><span class="sxs-lookup"><span data-stu-id="a5f62-157">[Boxing](../../csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span> <span data-ttu-id="a5f62-158">Autrement dit, vous allouez un objet pour contenir les données, puis retournez un pointeur vers cet objet.</span><span class="sxs-lookup"><span data-stu-id="a5f62-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span> <span data-ttu-id="a5f62-159">Le .NET Framework effectue parfois le boxing de certaines valeurs en raison de la signature d'une méthode ou du type d'un emplacement de stockage.</span><span class="sxs-lookup"><span data-stu-id="a5f62-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span> <span data-ttu-id="a5f62-160">L'encapsulation d'un type valeur dans un objet entraîne une allocation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="a5f62-160">Wrapping a value type in an object causes memory allocation.</span></span> <span data-ttu-id="a5f62-161">De nombreuses opérations de boxing peuvent favoriser l'allocation de méga-octets ou de giga-octets de mémoire dans votre application, ce qui signifie que cette dernière entraînera encore plus d'opérations de GC.</span><span class="sxs-lookup"><span data-stu-id="a5f62-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="a5f62-162">Le .NET Framework et les compilateurs de langage évitent le boxing autant que possible, mais parfois il intervient quand vous vous y attendez le moins.</span><span class="sxs-lookup"><span data-stu-id="a5f62-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span>
  
 <span data-ttu-id="a5f62-163">Pour voir le boxing dans PerfView, ouvrez une trace et examinez les piles d'allocation de tas GC sous le nom du processus de votre application (souvenez-vous, PerfView fournit des rapports sur tous les processus).</span><span class="sxs-lookup"><span data-stu-id="a5f62-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span> <span data-ttu-id="a5f62-164">Si vous voyez des types tels que <xref:System.Int32?displayProperty=nameWithType> et <xref:System.Char?displayProperty=nameWithType> sous les allocations, vous effectuez le boxing de types valeur.</span><span class="sxs-lookup"><span data-stu-id="a5f62-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span> <span data-ttu-id="a5f62-165">La sélection d'un de ces types vous montrera les piles et les fonctions dans lesquelles le boxing s'effectue.</span><span class="sxs-lookup"><span data-stu-id="a5f62-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span>
  
 <span data-ttu-id="a5f62-166">**Exemple 1 : méthodes string et arguments de type valeur**</span><span class="sxs-lookup"><span data-stu-id="a5f62-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="a5f62-167">Cet exemple de code illustre un boxing potentiellement inutile et excessif :</span><span class="sxs-lookup"><span data-stu-id="a5f62-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
```csharp  
public class Logger  
{  
    public static void WriteLine(string s) { /*...*/ }  
}  
  
public class BoxingExample  
{  
    public void Log(int id, int size)  
    {  
        var s = string.Format("{0}:{1}", id, size);  
        Logger.WriteLine(s);  
    }  
}  
```  
  
 <span data-ttu-id="a5f62-168">Ce code fournit des fonctionnalités de journalisation qui permettent à une application d'appeler la fonction `Log` fréquemment, éventuellement des millions de fois.</span><span class="sxs-lookup"><span data-stu-id="a5f62-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span> <span data-ttu-id="a5f62-169">Le problème est que l'appel de `string.Format` se traduit par la surcharge <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="a5f62-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span>
  
 <span data-ttu-id="a5f62-170">Cette surcharge oblige le .NET Framework à effectuer le boxing des valeurs `int` en objets pour les passer à cet appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="a5f62-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span> <span data-ttu-id="a5f62-171">Une correction partielle consiste à appeler `id.ToString()` et `size.ToString()`, et à passer toutes les chaînes (qui sont des objets) à l'appel de `string.Format`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span> <span data-ttu-id="a5f62-172">L'appel de `ToString()` n'alloue pas de chaîne, mais cette allocation aura lieu quoi qu'il en soit dans `string.Format`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span>
  
 <span data-ttu-id="a5f62-173">Vous pouvez considérer que cet appel élémentaire à `string.Format` est une simple concaténation de chaînes, et vous pouvez écrire le code suivant à la place :</span><span class="sxs-lookup"><span data-stu-id="a5f62-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="a5f62-174">Toutefois, cette ligne de code introduit une allocation de boxing car elle est compilée en <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span><span class="sxs-lookup"><span data-stu-id="a5f62-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span> <span data-ttu-id="a5f62-175">Le .NET Framework doit effectuer le boxing du littéral de caractère pour appeler `Concat`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="a5f62-176">**Correctif pour l’exemple 1**</span><span class="sxs-lookup"><span data-stu-id="a5f62-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="a5f62-177">Le correctif complet est simple.</span><span class="sxs-lookup"><span data-stu-id="a5f62-177">The complete fix is simple.</span></span> <span data-ttu-id="a5f62-178">Remplacez simplement le littéral de caractère par un littéral de chaîne. Cela n'entraîne pas de boxing car les chaînes sont déjà des objets :</span><span class="sxs-lookup"><span data-stu-id="a5f62-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="a5f62-179">**Exemple 2 : boxing d’enums**</span><span class="sxs-lookup"><span data-stu-id="a5f62-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="a5f62-180">Cet exemple était responsable de l'allocation d'une énorme quantité de mémoire dans les nouveaux compilateurs C# et Visual Basic en raison de l'utilisation fréquente des types énumération, notamment dans les opérations de consultation de dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="a5f62-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span>
  
```csharp  
public enum Color  
{  
    Red, Green, Blue  
}  
  
public class BoxingExample  
{  
    private string name;  
    private Color color;  
    public override int GetHashCode()  
    {  
        return name.GetHashCode() ^ color.GetHashCode();  
    }  
}  
```  
  
 <span data-ttu-id="a5f62-181">Ce problème est très subtil.</span><span class="sxs-lookup"><span data-stu-id="a5f62-181">This problem is very subtle.</span></span> <span data-ttu-id="a5f62-182">PerfView rapporterait cela en tant que boxing <xref:System.Enum.GetHashCode>, car la méthode effectue le boxing de la représentation sous-jacente du type énumération, pour des raisons d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="a5f62-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span> <span data-ttu-id="a5f62-183">Si vous examinez attentivement PerfView, vous pouvez voir deux allocations de boxing pour chaque appel à <xref:System.Enum.GetHashCode>.</span><span class="sxs-lookup"><span data-stu-id="a5f62-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span> <span data-ttu-id="a5f62-184">Le compilateur en insère une et le .NET Framework insère l'autre.</span><span class="sxs-lookup"><span data-stu-id="a5f62-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span>
  
 <span data-ttu-id="a5f62-185">**Correctif pour l’exemple 2**</span><span class="sxs-lookup"><span data-stu-id="a5f62-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="a5f62-186">Vous pouvez aisément éviter ces deux allocations en effectuant un cast vers la représentation sous-jacente avant d'appeler <xref:System.Enum.GetHashCode> :</span><span class="sxs-lookup"><span data-stu-id="a5f62-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="a5f62-187">Une autre source courante de boxing sur des types énumération est la méthode <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a5f62-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a5f62-188">L’argument passé à <xref:System.Enum.HasFlag%28System.Enum%29> doit faire l’objet du boxing.</span><span class="sxs-lookup"><span data-stu-id="a5f62-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span> <span data-ttu-id="a5f62-189">Dans la plupart des cas, le remplacement des appels à <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> par un test au niveau du bit est plus simple et n'entraîne pas d'allocation.</span><span class="sxs-lookup"><span data-stu-id="a5f62-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span>
  
 <span data-ttu-id="a5f62-190">Gardez à l'esprit le premier fait énoncé sur les performances (ne pas optimiser prématurément) et ne commencez pas à réécrire tout votre code de cette manière.</span><span class="sxs-lookup"><span data-stu-id="a5f62-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span> <span data-ttu-id="a5f62-191">Soyez conscient des coûts du boxing, mais modifiez votre code une fois seulement que vous aurez profilé votre application et trouvé les points sensibles.</span><span class="sxs-lookup"><span data-stu-id="a5f62-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span>
  
### <a name="strings"></a><span data-ttu-id="a5f62-192">Chaînes</span><span class="sxs-lookup"><span data-stu-id="a5f62-192">Strings</span></span>  
 <span data-ttu-id="a5f62-193">Les manipulations de chaînes comptent parmi les plus grands responsables d'allocations, et figurent souvent dans PerfView dans les cinq premières allocations.</span><span class="sxs-lookup"><span data-stu-id="a5f62-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span> <span data-ttu-id="a5f62-194">Les programmes utilisent des chaînes pour les interfaces API de sérialisation, JSON et REST.</span><span class="sxs-lookup"><span data-stu-id="a5f62-194">Programs use strings for serialization, JSON, and REST APIs.</span></span> <span data-ttu-id="a5f62-195">Vous pouvez utiliser des chaînes en tant que constantes de programmation pour interagir avec des systèmes quand vous ne pouvez pas utiliser les types énumération.</span><span class="sxs-lookup"><span data-stu-id="a5f62-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span> <span data-ttu-id="a5f62-196">Quand votre profilage montre que les chaînes affectent grandement les performances, recherchez les appels aux méthodes <xref:System.String> tels que <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, etc.</span><span class="sxs-lookup"><span data-stu-id="a5f62-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span> <span data-ttu-id="a5f62-197">Il est utile d'avoir recours à <xref:System.Text.StringBuilder> pour éviter le coût de la création d'une seule chaîne à partir de nombreux composants, mais même l'allocation de l'objet <xref:System.Text.StringBuilder> peut devenir un goulot d'étranglement que vous devrez gérer.</span><span class="sxs-lookup"><span data-stu-id="a5f62-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span>
  
 <span data-ttu-id="a5f62-198">**Exemple 3 : opérations de chaînes**</span><span class="sxs-lookup"><span data-stu-id="a5f62-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="a5f62-199">Le compilateur C# possédait ce code qui écrit le texte d'un commentaire de document XML formaté :</span><span class="sxs-lookup"><span data-stu-id="a5f62-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
```csharp  
public void WriteFormattedDocComment(string text)  
{  
    string[] lines = text.Split(new[] { "\r\n", "\r", "\n" },  
                                StringSplitOptions.None);  
    int numLines = lines.Length;  
    bool skipSpace = true;  
    if (lines[0].TrimStart().StartsWith("///"))  
    {  
        for (int i = 0; i < numLines; i++)  
        {  
            string trimmed = lines[i].TrimStart();  
            if (trimmed.Length < 4 || !char.IsWhiteSpace(trimmed[3]))  
            {  
                skipSpace = false;  
                break;  
            }  
        }  
        int substringStart = skipSpace ? 4 : 3;  
        for (int i = 0; i < numLines; i++)  
            WriteLine(lines[i].TrimStart().Substring(substringStart));  
    }  
    else { /* ... */ }  
```  
  
 <span data-ttu-id="a5f62-200">Vous pouvez constater que ce code effectue beaucoup de manipulations de chaînes.</span><span class="sxs-lookup"><span data-stu-id="a5f62-200">You can see that this code does a lot of string manipulation.</span></span> <span data-ttu-id="a5f62-201">Le code utilise des méthodes de bibliothèque pour séparer les lignes en chaînes distinctes, pour découper l’espace blanc, pour vérifier si l’argument `text` est un commentaire de documentation XML et pour extraire des sous-chaînes des lignes.</span><span class="sxs-lookup"><span data-stu-id="a5f62-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span>
  
 <span data-ttu-id="a5f62-202">À la première ligne dans `WriteFormattedDocComment`, l’appel `text.Split` alloue un nouveau tableau à trois éléments comme argument chaque fois qu’il est appelé.</span><span class="sxs-lookup"><span data-stu-id="a5f62-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span> <span data-ttu-id="a5f62-203">Le compilateur doit émettre du code pour allouer ce tableau chaque fois.</span><span class="sxs-lookup"><span data-stu-id="a5f62-203">The compiler has to emit code to allocate this array each time.</span></span> <span data-ttu-id="a5f62-204">En effet, le compilateur ne sait pas si <xref:System.String.Split%2A> stocke le tableau quelque part où il pourrait être modifié par un autre code, ce qui affecterait ultérieurement les appels à `WriteFormattedDocComment`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span> <span data-ttu-id="a5f62-205">L'appel à <xref:System.String.Split%2A> alloue également une chaîne pour chaque ligne dans `text` et alloue encore de la mémoire pour effectuer l'opération.</span><span class="sxs-lookup"><span data-stu-id="a5f62-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span>
  
 <span data-ttu-id="a5f62-206">`WriteFormattedDocComment` possède trois appels à la méthode <xref:System.String.TrimStart%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5f62-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span> <span data-ttu-id="a5f62-207">Deux se trouvent dans des boucles internes qui dupliquent le travail et les allocations.</span><span class="sxs-lookup"><span data-stu-id="a5f62-207">Two are in inner loops that duplicate work and allocations.</span></span> <span data-ttu-id="a5f62-208">Pour aggraver encore la situation, appeler la méthode <xref:System.String.TrimStart%2A> sans argument alloue un tableau vide (pour le paramètre `params`) en plus de la chaîne résultante.</span><span class="sxs-lookup"><span data-stu-id="a5f62-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span>
  
 <span data-ttu-id="a5f62-209">Enfin, il existe un appel à la méthode <xref:System.String.Substring%2A>, qui alloue habituellement une nouvelle chaîne.</span><span class="sxs-lookup"><span data-stu-id="a5f62-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span>
  
 <span data-ttu-id="a5f62-210">**Correctif pour l’exemple 3**</span><span class="sxs-lookup"><span data-stu-id="a5f62-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="a5f62-211">À la différence des exemples précédents, de petites modifications ne peuvent pas corriger ces allocations.</span><span class="sxs-lookup"><span data-stu-id="a5f62-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span> <span data-ttu-id="a5f62-212">Vous devez prendre du recul, examiner le problème et tenter une approche différente.</span><span class="sxs-lookup"><span data-stu-id="a5f62-212">You need to step back, look at the problem, and approach it differently.</span></span> <span data-ttu-id="a5f62-213">Par exemple, vous pouvez noter que l'argument pour `WriteFormattedDocComment()` est une chaîne qui possède toutes les informations dont la méthode a besoin, de sorte que le code pourrait effectuer une indexation supplémentaire au lieu d'allouer de nombreuses chaînes partielles.</span><span class="sxs-lookup"><span data-stu-id="a5f62-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span>
  
 <span data-ttu-id="a5f62-214">L’équipe de performances du compilateur s’est attaquée à toutes ces allocations avec du code similaire à :</span><span class="sxs-lookup"><span data-stu-id="a5f62-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
```csharp  
private int IndexOfFirstNonWhiteSpaceChar(string text, int start) {  
    while (start < text.Length && char.IsWhiteSpace(text[start])) start++;  
    return start;  
}  
  
private bool TrimmedStringStartsWith(string text, int start, string prefix) {  
    start = IndexOfFirstNonWhiteSpaceChar(text, start);  
    int len = text.Length - start;  
    if (len < prefix.Length) return false;  
    for (int i = 0; i < len; i++)  
    {  
        if (prefix[i] != text[start + i]) return false;  
    }  
    return true;  
}  
  
// etc...
```  
  
 <span data-ttu-id="a5f62-215">La première version de `WriteFormattedDocComment()` allouait un tableau, plusieurs sous-chaînes et une sous-chaîne tronquée avec un tableau `params` vide.</span><span class="sxs-lookup"><span data-stu-id="a5f62-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span> <span data-ttu-id="a5f62-216">Il a également vérifié pour "//".</span><span class="sxs-lookup"><span data-stu-id="a5f62-216">It also checked for "///".</span></span> <span data-ttu-id="a5f62-217">Le code révisé utilise uniquement l'indexation et n'alloue rien.</span><span class="sxs-lookup"><span data-stu-id="a5f62-217">The revised code uses only indexing and allocates nothing.</span></span> <span data-ttu-id="a5f62-218">Il trouve le premier personnage qui n’est pas l’espace blanc, puis vérifie caractère par personnage pour voir si la chaîne commence par "//".</span><span class="sxs-lookup"><span data-stu-id="a5f62-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with "///".</span></span> <span data-ttu-id="a5f62-219">Le nouveau `IndexOfFirstNonWhiteSpaceChar` code <xref:System.String.TrimStart%2A> utilise au lieu de retourner le premier index (après un index de démarrage spécifié) où un caractère non-espace blanc se produit.</span><span class="sxs-lookup"><span data-stu-id="a5f62-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-white-space character occurs.</span></span> <span data-ttu-id="a5f62-220">Le correctif n'est pas complet, mais vous pouvez voir comment appliquer des correctifs similaires pour obtenir une solution complète.</span><span class="sxs-lookup"><span data-stu-id="a5f62-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span> <span data-ttu-id="a5f62-221">En appliquant cette approche dans l'ensemble du code, vous pouvez supprimer toutes les allocations dans `WriteFormattedDocComment()`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span>
  
 <span data-ttu-id="a5f62-222">**Exemple 4 : StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="a5f62-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="a5f62-223">Cet exemple utilise un objet <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="a5f62-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span> <span data-ttu-id="a5f62-224">La fonction suivante génère un nom de type complet pour des types génériques :</span><span class="sxs-lookup"><span data-stu-id="a5f62-224">The following function generates a full type name for generic types:</span></span>  
  
```csharp  
public class Example  
{  
    // Constructs a name like "SomeType<T1, T2, T3>"  
    public string GenerateFullTypeName(string name, int arity)  
    {  
        StringBuilder sb = new StringBuilder();  
  
        sb.Append(name);  
        if (arity != 0)  
        {  
            sb.Append("<");  
            for (int i = 1; i < arity; i++)  
            {  
                sb.Append("T"); sb.Append(i.ToString()); sb.Append(", ");  
            }  
            sb.Append("T"); sb.Append(i.ToString()); sb.Append(">");  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
 <span data-ttu-id="a5f62-225">Le focus est sur la ligne qui crée une nouvelle instance <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="a5f62-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span> <span data-ttu-id="a5f62-226">Le code génère une allocation pour `sb.ToString()` et des allocations internes au sein de l'implémentation <xref:System.Text.StringBuilder>, mais vous ne pouvez pas contrôler ces allocations si vous souhaitez la chaîne résultante.</span><span class="sxs-lookup"><span data-stu-id="a5f62-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span>
  
 <span data-ttu-id="a5f62-227">**Correctif pour l’exemple 4**</span><span class="sxs-lookup"><span data-stu-id="a5f62-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="a5f62-228">Pour corriger l'allocation de l'objet `StringBuilder`, mettez en cache l'objet.</span><span class="sxs-lookup"><span data-stu-id="a5f62-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span> <span data-ttu-id="a5f62-229">Même la mise en cache d'une instance unique susceptible d'être jetée peut améliorer les performances de manière significative.</span><span class="sxs-lookup"><span data-stu-id="a5f62-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span> <span data-ttu-id="a5f62-230">Il s'agit de la nouvelle implémentation de la fonction, qui omet tout le code à l'exception des nouvelles première et dernière lignes :</span><span class="sxs-lookup"><span data-stu-id="a5f62-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="a5f62-231">Les composants clés sont les nouvelles fonctions `AcquireBuilder()` et `GetStringAndReleaseBuilder()` :</span><span class="sxs-lookup"><span data-stu-id="a5f62-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
```csharp  
[ThreadStatic]  
private static StringBuilder cachedStringBuilder;  
  
private static StringBuilder AcquireBuilder()  
{  
    StringBuilder result = cachedStringBuilder;  
    if (result == null)  
    {  
        return new StringBuilder();  
    }  
    result.Clear();  
    cachedStringBuilder = null;  
    return result;  
}  
  
private static string GetStringAndReleaseBuilder(StringBuilder sb)  
{  
    string result = sb.ToString();  
    cachedStringBuilder = sb;  
    return result;  
}  
```  
  
 <span data-ttu-id="a5f62-232">Comme les nouveaux compilateurs utilisent le threading, ces implémentations utilisent un champ static de thread (attribut <xref:System.ThreadStaticAttribute>) pour mettre en cache <xref:System.Text.StringBuilder>, et vous pouvez probablement vous passer de la déclaration `ThreadStatic`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span> <span data-ttu-id="a5f62-233">Le champ static de thread contient une valeur unique pour chaque thread qui exécute ce code.</span><span class="sxs-lookup"><span data-stu-id="a5f62-233">The thread-static field holds a unique value for each thread that executes this code.</span></span>
  
 <span data-ttu-id="a5f62-234">`AcquireBuilder()` retourne l'instance <xref:System.Text.StringBuilder> mise en cache, le cas échéant, après l'avoir effacée et avoir défini le champ ou le cache sur Null.</span><span class="sxs-lookup"><span data-stu-id="a5f62-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span> <span data-ttu-id="a5f62-235">Dans le cas contraire, `AcquireBuilder()` crée une nouvelle instance et la retourne, laissant le champ ou le cache défini sur Null.</span><span class="sxs-lookup"><span data-stu-id="a5f62-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span>
  
 <span data-ttu-id="a5f62-236">Une fois que vous avez terminé avec <xref:System.Text.StringBuilder>, vous appelez `GetStringAndReleaseBuilder()` pour obtenir la chaîne résultante, enregistrez l'instance <xref:System.Text.StringBuilder> dans le champ ou le cache, puis retournez le résultat.</span><span class="sxs-lookup"><span data-stu-id="a5f62-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span> <span data-ttu-id="a5f62-237">Il est possible pour l'exécution d'entrer une nouvelle fois ce code et de créer plusieurs objets <xref:System.Text.StringBuilder> (bien que cela se produise rarement).</span><span class="sxs-lookup"><span data-stu-id="a5f62-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span> <span data-ttu-id="a5f62-238">Le code enregistre uniquement la dernière instance <xref:System.Text.StringBuilder> libérée pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="a5f62-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span> <span data-ttu-id="a5f62-239">Cette stratégie de mise en cache simple a réduit considérablement les allocations dans les nouveaux compilateurs.</span><span class="sxs-lookup"><span data-stu-id="a5f62-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span> <span data-ttu-id="a5f62-240">Certains composants de .NET Framework et de MSBuild (« MSBuild ») utilisent une technique similaire pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="a5f62-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span>
  
 <span data-ttu-id="a5f62-241">Cette stratégie de mise en cache simple est conforme à une conception de cache satisfaisante car elle possède une taille seuil.</span><span class="sxs-lookup"><span data-stu-id="a5f62-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span> <span data-ttu-id="a5f62-242">Toutefois, il y a plus de code maintenant que dans l'original, ce qui induit des coûts de maintenance supérieurs.</span><span class="sxs-lookup"><span data-stu-id="a5f62-242">However, there is more code now than in the original, which means more maintenance costs.</span></span> <span data-ttu-id="a5f62-243">Vous devez adopter la stratégie de mise en cache seulement si vous avez trouvé un problème de performances et que PerfView a montré que les allocations <xref:System.Text.StringBuilder> constituent un contributeur important.</span><span class="sxs-lookup"><span data-stu-id="a5f62-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span>
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="a5f62-244">Expressions LINQ et lambda</span><span class="sxs-lookup"><span data-stu-id="a5f62-244">LINQ and lambdas</span></span>  
<span data-ttu-id="a5f62-245">La requête intégrée en langue (LINQ), en conjonction avec les expressions lambda, est un exemple de caractéristique de productivité.</span><span class="sxs-lookup"><span data-stu-id="a5f62-245">Language-Integrated Query (LINQ), in conjunction with lambda expressions, is an example of a productivity feature.</span></span> <span data-ttu-id="a5f62-246">Cependant, son utilisation peut avoir un impact significatif sur les performances au fil du temps, et vous pourriez trouver que vous devez réécrire votre code.</span><span class="sxs-lookup"><span data-stu-id="a5f62-246">However, its use may have a significant impact on performance over time, and you might find you need to rewrite your code.</span></span>
  
 <span data-ttu-id="a5f62-247">**Exemple 5 : expressions lambda, liste\<T> et IEnumerable\<T>**</span><span class="sxs-lookup"><span data-stu-id="a5f62-247">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="a5f62-248">Cet exemple utilise du [code de style opérationnel et LINQ](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) pour rechercher un symbole dans le modèle du compilateur, selon une chaîne de nom :</span><span class="sxs-lookup"><span data-stu-id="a5f62-248">This example uses [LINQ and functional style code](https://docs.microsoft.com/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
```csharp  
class Symbol {  
    public string Name { get; private set; }  
    /*...*/  
}  
  
class Compiler {  
    private List<Symbol> symbols;  
    public Symbol FindMatchingSymbol(string name)  
    {  
        return symbols.FirstOrDefault(s => s.Name == name);  
    }  
}  
```  
  
 <span data-ttu-id="a5f62-249">Le nouveau compilateur et les expériences IDE construites dessus appellent `FindMatchingSymbol()` très fréquemment, et il existe plusieurs allocations masquées dans la seule ligne de code de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="a5f62-249">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span> <span data-ttu-id="a5f62-250">Pour examiner ces allocations, commencer par séparer la seule ligne de code de la fonction en deux lignes :</span><span class="sxs-lookup"><span data-stu-id="a5f62-250">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="a5f62-251">Dans la première ligne, l’[expression lambda](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [ se ferme par-dessus](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) la variable locale `name`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-251">In the first line, the [lambda expression](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` [closes over](https://docs.microsoft.com/archive/blogs/ericlippert/what-are-closures) the local variable `name`.</span></span> <span data-ttu-id="a5f62-252">Cela signifie qu’en plus d’allouer un objet pour le [délégué](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) contenu dans `predicate`, le code alloue une classe statique pour contenir l’environnement qui capture la valeur de `name`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-252">This means that in addition to allocating an object for the [delegate](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span> <span data-ttu-id="a5f62-253">Le compilateur génère un code similaire au suivant :</span><span class="sxs-lookup"><span data-stu-id="a5f62-253">The compiler generates code like the following:</span></span>  
  
```csharp  
// Compiler-generated class to hold environment state for lambda  
private class Lambda1Environment  
{  
    public string capturedName;  
    public bool Evaluate(Symbol s)  
    {  
        return s.Name == this.capturedName;  
    }  
}  
  
// Expanded Func<Symbol, bool> predicate = s => s.Name == name;  
Lambda1Environment l = new Lambda1Environment() { capturedName = name };  
var predicate = new Func<Symbol, bool>(l.Evaluate);  
```  
  
 <span data-ttu-id="a5f62-254">Les deux allocations `new` (une pour la classe d'environnement et l'autre pour le délégué) sont désormais explicites.</span><span class="sxs-lookup"><span data-stu-id="a5f62-254">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span>
  
 <span data-ttu-id="a5f62-255">À présent, examinez l'appel à `FirstOrDefault`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-255">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="a5f62-256">Cette méthode d'extension sur le type <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> induit également une allocation.</span><span class="sxs-lookup"><span data-stu-id="a5f62-256">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span> <span data-ttu-id="a5f62-257">Comme `FirstOrDefault` accepte un objet <xref:System.Collections.Generic.IEnumerable%601> comme premier argument, vous pouvez développer l'appel au code suivant (légèrement simplifié pour cette présentation) :</span><span class="sxs-lookup"><span data-stu-id="a5f62-257">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
```csharp  
// Expanded return symbols.FirstOrDefault(predicate) ...
     IEnumerable<Symbol> enumerable = symbols;  
     IEnumerator<Symbol> enumerator = enumerable.GetEnumerator();  
     while(enumerator.MoveNext())  
     {  
         if (predicate(enumerator.Current))  
             return enumerator.Current;  
     }  
     return default(Symbol);  
```  
  
 <span data-ttu-id="a5f62-258">La variable `symbols` possède le type <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="a5f62-258">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="a5f62-259">Le type de collection <xref:System.Collections.Generic.List%601> implémente <xref:System.Collections.Generic.IEnumerable%601> et définit intelligemment un énumérateur (interface <xref:System.Collections.Generic.IEnumerator%601>) que <xref:System.Collections.Generic.List%601> implémente avec un `struct`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-259">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span> <span data-ttu-id="a5f62-260">L'utilisation d'une structure à la place d'une classe signifie que vous évitez habituellement toutes les allocations de tas, lesquelles, à leur tour, peuvent affecter les performances de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a5f62-260">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span> <span data-ttu-id="a5f62-261">Les énumérateurs sont généralement utilisés avec la boucle `foreach` du langage, qui utilise la structure des énumérateurs lorsqu'elle est renvoyée sur la pile d'appels.</span><span class="sxs-lookup"><span data-stu-id="a5f62-261">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span> <span data-ttu-id="a5f62-262">L'incrémentation du pointeur de la pile d'appels pour faire de la place pour un objet n'affecte pas le GC comme le fait une allocation de tas.</span><span class="sxs-lookup"><span data-stu-id="a5f62-262">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span>
  
 <span data-ttu-id="a5f62-263">Dans le cas de l'appel `FirstOrDefault` développé, le code a besoin d'appeler `GetEnumerator()` sur un <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="a5f62-263">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="a5f62-264">L'affectation de `symbols` à la variable `enumerable` du type `IEnumerable<Symbol>` entraîne la perte des informations indiquant que l'objet réel est un <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="a5f62-264">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="a5f62-265">Cela signifie que quand le code récupère l’énumérateur avec `enumerable.GetEnumerator()`, le .NET Framework doit effectuer le boxing de la structure renvoyée pour l’affecter à la variable `enumerator`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-265">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span>
  
 <span data-ttu-id="a5f62-266">**Correctif pour l’exemple 5**</span><span class="sxs-lookup"><span data-stu-id="a5f62-266">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="a5f62-267">Le correctif consiste à réécrire `FindMatchingSymbol` comme suit, en remplaçant sa ligne de code unique par six lignes de code qui restent concises, faciles à lire et à comprendre, et aisées à tenir à jour :</span><span class="sxs-lookup"><span data-stu-id="a5f62-267">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
```csharp  
public Symbol FindMatchingSymbol(string name)  
    {  
        foreach (Symbol s in symbols)  
        {  
            if (s.Name == name)  
                return s;  
        }  
        return null;  
    }  
```  
  
 <span data-ttu-id="a5f62-268">Ce code n'utilise pas d'énumérateurs, d'expressions lambda ni de méthodes d'extension LINQ, et il n'induit pas d'allocations.</span><span class="sxs-lookup"><span data-stu-id="a5f62-268">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span> <span data-ttu-id="a5f62-269">L’absence d’allocation vient du fait que le compilateur peut voir que la collection `symbols` est une classe <xref:System.Collections.Generic.List%601> et qu’elle peut lier l’énumérateur résultant (une structure) à une variable locale avec le type correct pour éviter le boxing.</span><span class="sxs-lookup"><span data-stu-id="a5f62-269">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span> <span data-ttu-id="a5f62-270">La version originale de cette fonction était un exemple parfait de la puissance expressive de C# et de la productivité du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a5f62-270">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span> <span data-ttu-id="a5f62-271">Cette nouvelle version, plus efficace, conserve ces qualités sans ajouter de code complexe à tenir à jour.</span><span class="sxs-lookup"><span data-stu-id="a5f62-271">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span>
  
### <a name="async-method-caching"></a><span data-ttu-id="a5f62-272">Mise en cache dans les méthodes async</span><span class="sxs-lookup"><span data-stu-id="a5f62-272">Async method caching</span></span>  

<span data-ttu-id="a5f62-273">L’exemple suivant illustre un problème courant qui se produit quand vous essayez d’utiliser des résultats en cache dans une méthode [async](../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="a5f62-273">The next example shows a common problem when you try to use cached results in an [async](../../csharp/programming-guide/concepts/async/index.md) method.</span></span>
  
 <span data-ttu-id="a5f62-274">**Exemple 6 : mise en cache dans les méthodes async**</span><span class="sxs-lookup"><span data-stu-id="a5f62-274">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="a5f62-275">Les fonctionnalités IDE de Visual Studio qui s'appuient sur les nouveaux compilateurs C# et Visual Basic récupèrent fréquemment des arborescences de syntaxe, et les compilateurs utilisent async à cette occasion pour maintenir la réactivité de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5f62-275">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span> <span data-ttu-id="a5f62-276">Voici la première version du code que vous pouvez écrire afin d'obtenir une arborescence de syntaxe :</span><span class="sxs-lookup"><span data-stu-id="a5f62-276">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
```csharp  
class SyntaxTree { /*...*/ }  
  
class Parser { /*...*/  
    public SyntaxTree Syntax { get; }  
    public Task ParseSourceCode() { /*...*/ }  
}  
  
class Compilation { /*...*/  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="a5f62-277">Vous pouvez voir que l'appel à `GetSyntaxTreeAsync()` instancie un `Parser`, analyse le code, puis retourne un objet <xref:System.Threading.Tasks.Task>, `Task<SyntaxTree>`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-277">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span> <span data-ttu-id="a5f62-278">La partie coûteuse correspond à l'allocation de l'instance `Parser` et à l'analyse du code.</span><span class="sxs-lookup"><span data-stu-id="a5f62-278">The expensive part is allocating the `Parser` instance and parsing the code.</span></span> <span data-ttu-id="a5f62-279">La fonction retourne une classe <xref:System.Threading.Tasks.Task> afin que les appelants puissent attendre le travail d'analyse et libérer le thread d'interface utilisateur pour être réactifs à l'entrée d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a5f62-279">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span>
  
 <span data-ttu-id="a5f62-280">Plusieurs fonctionnalités Visual Studio peuvent essayer d’obtenir la même arborescence de syntaxe. Vous pouvez donc écrire le code suivant pour mettre en cache le résultat d’analyse pour économiser du temps et des allocations.</span><span class="sxs-lookup"><span data-stu-id="a5f62-280">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span> <span data-ttu-id="a5f62-281">Toutefois, ce code induit une allocation :</span><span class="sxs-lookup"><span data-stu-id="a5f62-281">However, this code incurs an allocation:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private SyntaxTree cachedResult;  
  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        if (this.cachedResult == null)  
        {  
            var parser = new Parser(); // allocation  
            await parser.ParseSourceCode(); // expensive  
            this.cachedResult = parser.Syntax;  
        }  
        return this.cachedResult;  
    }  
}  
```  
  
 <span data-ttu-id="a5f62-282">Vous constatez que le nouveau code avec la mise en cache possède un champ `SyntaxTree` nommé `cachedResult`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-282">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span> <span data-ttu-id="a5f62-283">Quand ce champ à la valeur null, `GetSyntaxTreeAsync()` effectue le travail et enregistre le résultat dans le cache.</span><span class="sxs-lookup"><span data-stu-id="a5f62-283">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span> <span data-ttu-id="a5f62-284">`GetSyntaxTreeAsync()` retourne l'objet `SyntaxTree`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-284">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span> <span data-ttu-id="a5f62-285">Le problème tient au fait que lorsque vous avez une fonction `async` de type `Task<SyntaxTree>` et que vous retournez une valeur de type `SyntaxTree`, le compilateur émet du code pour allouer un objet Task pour contenir le résultat (en utilisant `Task<SyntaxTree>.FromResult()`).</span><span class="sxs-lookup"><span data-stu-id="a5f62-285">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span> <span data-ttu-id="a5f62-286">L’objet Task est marqué comme terminé et le résultat est disponible immédiatement.</span><span class="sxs-lookup"><span data-stu-id="a5f62-286">The Task is marked as completed, and the result is immediately available.</span></span> <span data-ttu-id="a5f62-287">Dans le code pour les nouveaux compilateurs, des objets <xref:System.Threading.Tasks.Task> déjà terminés se manifestaient si souvent que la correction de ces allocations a amélioré notablement la réactivité.</span><span class="sxs-lookup"><span data-stu-id="a5f62-287">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span>
  
 <span data-ttu-id="a5f62-288">**Correctif pour l’exemple 6**</span><span class="sxs-lookup"><span data-stu-id="a5f62-288">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="a5f62-289">Pour supprimer <xref:System.Threading.Tasks.Task> l’allocation complétée, vous pouvez mettre en cache l’objet Task avec le résultat terminé :</span><span class="sxs-lookup"><span data-stu-id="a5f62-289">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private Task<SyntaxTree> cachedResult;  
  
    public Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        return this.cachedResult ??
               (this.cachedResult = GetSyntaxTreeUncachedAsync());  
    }  
  
    private async Task<SyntaxTree> GetSyntaxTreeUncachedAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="a5f62-290">Ce code change le type de `cachedResult` en `Task<SyntaxTree>` et emploie une fonction d'assistance `async` qui contient le code original issu de `GetSyntaxTreeAsync()`.</span><span class="sxs-lookup"><span data-stu-id="a5f62-290">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span> <span data-ttu-id="a5f62-291">`GetSyntaxTreeAsync()` utilise maintenant l’[opérateur de fusion Null](../../csharp/language-reference/operators/null-coalescing-operator.md) pour retourner `cachedResult` s’il n’a pas la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="a5f62-291">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span> <span data-ttu-id="a5f62-292">Si `cachedResult` a la valeur Null, alors `GetSyntaxTreeAsync()` appelle `GetSyntaxTreeUncachedAsync()` et met en cache le résultat.</span><span class="sxs-lookup"><span data-stu-id="a5f62-292">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span> <span data-ttu-id="a5f62-293">Notez que `GetSyntaxTreeAsync()` n'attend pas l'appel à `GetSyntaxTreeUncachedAsync()` comme le ferait normalement le code.</span><span class="sxs-lookup"><span data-stu-id="a5f62-293">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span> <span data-ttu-id="a5f62-294">Ne pas utiliser d'attente signifie que quand `GetSyntaxTreeUncachedAsync()` retourne son objet <xref:System.Threading.Tasks.Task>, `GetSyntaxTreeAsync()` retourne immédiatement l'objet <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="a5f62-294">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="a5f62-295">À présent, le résultat mis en cache est un objet <xref:System.Threading.Tasks.Task>, d'où l'absence d'allocation pour retourner le résultat mis en cache.</span><span class="sxs-lookup"><span data-stu-id="a5f62-295">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span>
  
### <a name="additional-considerations"></a><span data-ttu-id="a5f62-296">Considérations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a5f62-296">Additional considerations</span></span>  
 <span data-ttu-id="a5f62-297">Vous trouverez ci-dessous quelques points supplémentaires concernant des problèmes susceptibles de survenir dans des applications volumineuses ou qui traitent de grandes quantités de données.</span><span class="sxs-lookup"><span data-stu-id="a5f62-297">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span>
  
 <span data-ttu-id="a5f62-298">**Dictionnaires**</span><span class="sxs-lookup"><span data-stu-id="a5f62-298">**Dictionaries**</span></span>  
  
 <span data-ttu-id="a5f62-299">Les dictionnaires sont utilisés de façon omniprésente dans de nombreux programmes. Malgré cela, ils sont très pratiques et intrinsèquement efficaces.</span><span class="sxs-lookup"><span data-stu-id="a5f62-299">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span> <span data-ttu-id="a5f62-300">Toutefois, ils sont souvent utilisés de façon inappropriée.</span><span class="sxs-lookup"><span data-stu-id="a5f62-300">However, they’re often used inappropriately.</span></span> <span data-ttu-id="a5f62-301">Dans Visual Studio et les nouveaux compilateurs, l'analyse montre qu'un grand nombre des dictionnaires contenaient un seul élément ou étaient vides.</span><span class="sxs-lookup"><span data-stu-id="a5f62-301">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span> <span data-ttu-id="a5f62-302">Un objet <xref:System.Collections.Generic.Dictionary%602> vide possède dix champs et occupe 48 octets sur le tas, sur un ordinateur x86.</span><span class="sxs-lookup"><span data-stu-id="a5f62-302">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span> <span data-ttu-id="a5f62-303">Les dictionnaires sont très utiles lorsque vous avez besoin d'un mappage ou d'une structure de données associative avec une recherche constante.</span><span class="sxs-lookup"><span data-stu-id="a5f62-303">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span> <span data-ttu-id="a5f62-304">Toutefois, quand vous ne possédez que quelques éléments, vous gaspillez beaucoup d'espace en utilisant un dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="a5f62-304">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span> <span data-ttu-id="a5f62-305">À la place, par exemple, vous pourriez examiner de façon itérative un `List<KeyValuePair\<K,V>>`, tout aussi rapidement.</span><span class="sxs-lookup"><span data-stu-id="a5f62-305">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span> <span data-ttu-id="a5f62-306">Si vous utilisez un dictionnaire seulement pour le charger avec des données, puis lire à partir de cet objet (un modèle très courant), l’utilisation d’un tableau trié avec une recherche N(log(N)) peut être quasiment aussi rapide, selon le nombre d’éléments que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="a5f62-306">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span>
  
 <span data-ttu-id="a5f62-307">**Classes et structures**</span><span class="sxs-lookup"><span data-stu-id="a5f62-307">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="a5f62-308">D'une certaine façon, les classes et les structures fournissent un compromis standard entre espace et temps pour le réglage de vos applications.</span><span class="sxs-lookup"><span data-stu-id="a5f62-308">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span> <span data-ttu-id="a5f62-309">Les classes induisent une surcharge de 12 octets sur un ordinateur x86 même si elles ne possèdent pas de champ, mais elles n'induisent pas de coût pour être passées, car seul un pointeur est nécessaire pour faire référence à une instance de classe.</span><span class="sxs-lookup"><span data-stu-id="a5f62-309">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span> <span data-ttu-id="a5f62-310">Les structures n'induisent pas d'allocations de tas si elles ne font pas l'objet d'un boxing, mais quand vous passez de grandes structures en tant qu'arguments de fonction ou valeurs de retour, la copie atomique de toutes les données membres des structures consomme du temps processeur.</span><span class="sxs-lookup"><span data-stu-id="a5f62-310">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span> <span data-ttu-id="a5f62-311">Surveillez les appels répétés à des propriétés qui retournent des structures et mettez en cache la valeur de la propriété dans une variable locale pour éviter la copie excessive de données.</span><span class="sxs-lookup"><span data-stu-id="a5f62-311">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span>
  
 <span data-ttu-id="a5f62-312">**Caches**</span><span class="sxs-lookup"><span data-stu-id="a5f62-312">**Caches**</span></span>  
  
 <span data-ttu-id="a5f62-313">Une astuce courante liée aux performances consiste à mettre en cache les résultats.</span><span class="sxs-lookup"><span data-stu-id="a5f62-313">A common performance trick is to cache results.</span></span> <span data-ttu-id="a5f62-314">Toutefois, un cache dépourvu d'une taille seuil ou d'une stratégie de suppression peut engendrer une fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="a5f62-314">However, a cache without a size cap or disposal policy can be a memory leak.</span></span> <span data-ttu-id="a5f62-315">Quand vous traitez de grandes quantités de données, si vous conservez une grande quantité de mémoire dans des caches, le garbage collection risque de contrebalancer les avantages de vos recherches en cache.</span><span class="sxs-lookup"><span data-stu-id="a5f62-315">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span>
  
 <span data-ttu-id="a5f62-316">Dans cet article, nous avons vu que vous devez être conscient des symptômes de goulot d'étranglement de performances qui peuvent affecter la réactivité de votre application, notamment pour les grands systèmes et les systèmes qui traitent de grandes quantités de données.</span><span class="sxs-lookup"><span data-stu-id="a5f62-316">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="a5f62-317">Les facteurs courants incluent le boxing, les manipulations de chaînes, les expressions LINQ et lambda, la mise en cache dans les méthodes async, la mise en cache sans taille limite ou stratégie de suppression, l'utilisation inappropriée des dictionnaires et le fait de passer des structures.</span><span class="sxs-lookup"><span data-stu-id="a5f62-317">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span> <span data-ttu-id="a5f62-318">Gardez à l'esprit les quatre faits liés au réglage de vos applications :</span><span class="sxs-lookup"><span data-stu-id="a5f62-318">Keep in mind the four facts for tuning your apps:</span></span>  
  
- <span data-ttu-id="a5f62-319">N'optimisez pas prématurément : soyez productif et réglez votre application quand vous détectez des problèmes.</span><span class="sxs-lookup"><span data-stu-id="a5f62-319">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span>
  
- <span data-ttu-id="a5f62-320">Les profils ne trompent pas : sans mesures, vous ne faites que supposer.</span><span class="sxs-lookup"><span data-stu-id="a5f62-320">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span>
  
- <span data-ttu-id="a5f62-321">Des outils efficaces font toute la différence : téléchargez PerfView et essayez-le.</span><span class="sxs-lookup"><span data-stu-id="a5f62-321">Good tools make all the difference – download PerfView and try it out.</span></span>
  
- <span data-ttu-id="a5f62-322">Tout se résume aux allocations : c'est dans ce domaine que l'équipe chargée de la plateforme des compilateurs a passé le plus de temps à améliorer les performances des nouveaux compilateurs.</span><span class="sxs-lookup"><span data-stu-id="a5f62-322">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a5f62-323">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5f62-323">See also</span></span>

- [<span data-ttu-id="a5f62-324">Vidéo de présentation de cette rubrique</span><span class="sxs-lookup"><span data-stu-id="a5f62-324">Video of presentation of this topic</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [<span data-ttu-id="a5f62-325">Guide des débutants sur le profilage des performances</span><span class="sxs-lookup"><span data-stu-id="a5f62-325">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [<span data-ttu-id="a5f62-326">Performances</span><span class="sxs-lookup"><span data-stu-id="a5f62-326">Performance</span></span>](index.md)
- <span data-ttu-id="a5f62-327">[Conseils relatifs aux performances .NET](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span><span class="sxs-lookup"><span data-stu-id="a5f62-327">[.NET Performance Tips](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v%3dmsdn.10))</span></span>
- [<span data-ttu-id="a5f62-328">Didacticiels PerfView sur Canal 9</span><span class="sxs-lookup"><span data-stu-id="a5f62-328">Channel 9 PerfView tutorials</span></span>](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [<span data-ttu-id="a5f62-329">Kit SDK .NET Compiler Platform</span><span class="sxs-lookup"><span data-stu-id="a5f62-329">The .NET Compiler Platform SDK</span></span>](../../csharp/roslyn-sdk/index.md)
- [<span data-ttu-id="a5f62-330">dotnet/roslyn repo sur GitHub</span><span class="sxs-lookup"><span data-stu-id="a5f62-330">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
