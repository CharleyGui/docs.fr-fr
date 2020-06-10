---
title: Création de threads et passage de données au démarrage
description: Apprenez à créer des threads et à passer des données à l’heure de début d’un processus de système d’exploitation dans .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
ms.openlocfilehash: 811028d3c853441ff3a61d3628a44e5c65ba7059
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661912"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="fc5c5-103">Création de threads et passage de données au démarrage</span><span class="sxs-lookup"><span data-stu-id="fc5c5-103">Creating threads and passing data at start time</span></span>

<span data-ttu-id="fc5c5-104">Lorsqu’un processus de système d’exploitation est créé, le système d’exploitation injecte un thread pour exécuter du code dans ce processus, y compris un domaine d’application d’origine.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-104">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="fc5c5-105">À ce stade, des domaines d’application peuvent être créés et détruits sans nécessairement avoir à créer ou à détruire des threads de système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-105">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="fc5c5-106">Si le code en cours d’exécution est un code géré, un objet <xref:System.Threading.Thread> pour le thread s’exécutant dans le domaine d’application actuel peut être obtenu en récupérant la propriété statique <xref:System.Threading.Thread.CurrentThread%2A> de type <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-106">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="fc5c5-107">Cette rubrique décrit la création de threads et présente des alternatives pour transmettre des données à la procédure de thread.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-107">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="fc5c5-108">Création d’un thread</span><span class="sxs-lookup"><span data-stu-id="fc5c5-108">Creating a thread</span></span>

 <span data-ttu-id="fc5c5-109">La création d’un nouvel objet <xref:System.Threading.Thread> entraîne la création d’un thread managé.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-109">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="fc5c5-110">La classe <xref:System.Threading.Thread> a des constructeurs qui acceptent un délégué <xref:System.Threading.ThreadStart> ou <xref:System.Threading.ParameterizedThreadStart> ; le délégué inclut dans un wrapper la méthode qui est appelée par le nouveau thread lorsque vous appelez la méthode <xref:System.Threading.Thread.Start%2A>.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-110">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="fc5c5-111">L’appel de <xref:System.Threading.Thread.Start%2A> plus d’une fois entraîne la levée d’une <xref:System.Threading.ThreadStateException>.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-111">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="fc5c5-112">La méthode <xref:System.Threading.Thread.Start%2A> est retournée immédiatement, souvent avant que le nouveau thread n’ait réellement démarré.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-112">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="fc5c5-113">Vous pouvez utiliser les propriétés <xref:System.Threading.Thread.ThreadState%2A> et <xref:System.Threading.Thread.IsAlive%2A> pour déterminer l’état du thread à tout moment, mais ces propriétés ne doivent jamais être utilisées pour synchroniser les activités de threads.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-113">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc5c5-114">Une fois qu’un thread a démarré, il n’est pas nécessaire de conserver une référence à l’objet <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-114">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="fc5c5-115">Le thread continue à s’exécuter jusqu'à la fin de la procédure de thread.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-115">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="fc5c5-116">L’exemple de code suivant crée deux nouveaux threads pour appeler des méthodes statiques et d’instance sur un autre objet.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-116">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a><span data-ttu-id="fc5c5-117">Passage de données à des threads</span><span class="sxs-lookup"><span data-stu-id="fc5c5-117">Passing data to threads</span></span>

 <span data-ttu-id="fc5c5-118">Dans la version 2.0 de .NET Framework, le délégué <xref:System.Threading.ParameterizedThreadStart> permet de transmettre facilement un objet contenant des données à un thread lorsque vous appelez la surcharge de la méthode <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-118">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="fc5c5-119">Pour obtenir un exemple de code, consultez <xref:System.Threading.ParameterizedThreadStart>.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-119">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="fc5c5-120">L’utilisation du délégué <xref:System.Threading.ParameterizedThreadStart> n’est pas une méthode de type sécurisé pour transmettre des données, car la surcharge de la méthode <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> accepte tous les objets.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-120">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="fc5c5-121">Une alternative consiste à encapsuler la procédure de thread et les données dans une classe d’assistance et à utiliser le délégué <xref:System.Threading.ThreadStart> pour exécuter la procédure de thread.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-121">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="fc5c5-122">L’exemple suivant montre cette technique :</span><span class="sxs-lookup"><span data-stu-id="fc5c5-122">The following example demonstrates this technique:</span></span>

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<span data-ttu-id="fc5c5-123">Ni le délégué <xref:System.Threading.ThreadStart> ni le délégué <xref:System.Threading.ParameterizedThreadStart> n’ont de valeur de retour, car il n’existe pas d’endroit où retourner les données provenant d’un appel asynchrone.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-123">Neither <xref:System.Threading.ThreadStart> nor <xref:System.Threading.ParameterizedThreadStart> delegate has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="fc5c5-124">Pour récupérer les résultats d’une méthode de thread, vous pouvez utiliser une méthode de rappel, comme montré dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-124">To retrieve the results of a thread method, you can use a callback method, as shown in the next section.</span></span>
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a><span data-ttu-id="fc5c5-125">Récupération de données provenant de threads avec des méthodes de rappel</span><span class="sxs-lookup"><span data-stu-id="fc5c5-125">Retrieving data from threads with callback methods</span></span>

 <span data-ttu-id="fc5c5-126">L’exemple suivant montre une méthode de rappel qui récupère des données à partir d’un thread.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-126">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="fc5c5-127">Le constructeur de la classe qui contient les données et la méthode de thread accepte également un délégué représentant la méthode de rappel ; avant la fin de la méthode de thread, il appelle le délégué de rappel.</span><span class="sxs-lookup"><span data-stu-id="fc5c5-127">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="fc5c5-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc5c5-128">See also</span></span>

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fc5c5-129">Threads</span><span class="sxs-lookup"><span data-stu-id="fc5c5-129">Threading</span></span>](index.md)
- [<span data-ttu-id="fc5c5-130">Utilisation des threads et du threading</span><span class="sxs-lookup"><span data-stu-id="fc5c5-130">Using Threads and Threading</span></span>](using-threads-and-threading.md)
