---
title: Constructeurs statiques - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 110d83caad0c588fa899a4129897784e9c74aab8
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881916"
---
# <a name="static-constructors-c-programming-guide"></a><span data-ttu-id="6a2a2-102">Constructeurs statiques (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6a2a2-102">Static Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="6a2a2-103">Un constructeur statique est utilisé pour initialiser des données [statiques](../../../csharp/language-reference/keywords/static.md) ou pour effectuer une action particulière qui ne doit être effectuée qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-103">A static constructor is used to initialize any [static](../../../csharp/language-reference/keywords/static.md) data, or to perform a particular action that needs to be performed once only.</span></span> <span data-ttu-id="6a2a2-104">Il est automatiquement appelé avant la création de la première instance ou le référencement d’un membre statique.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-104">It is called automatically before the first instance is created or any static members are referenced.</span></span>  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  
  
 <span data-ttu-id="6a2a2-105">Les constructeurs statiques ont les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a2a2-105">Static constructors have the following properties:</span></span>  
  
- <span data-ttu-id="6a2a2-106">Un constructeur statique n’accepte pas de modificateur d’accès et n’a pas de paramètre.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-106">A static constructor does not take access modifiers or have parameters.</span></span>  
  
- <span data-ttu-id="6a2a2-107">Un constructeur statique est automatiquement appelé pour initialiser la [classe](../../../csharp/language-reference/keywords/class.md) avant la création de la première instance ou le référencement d’un membre statique.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-107">A static constructor is called automatically to initialize the [class](../../../csharp/language-reference/keywords/class.md) before the first instance is created or any static members are referenced.</span></span> <span data-ttu-id="6a2a2-108">Notez que le constructeur statique d’un type est appelé quand une méthode statique assignée à un événement ou un délégué est appelée, et non pas quand elle est assignée.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-108">Note that a type's static constructor is called when a static method assigned to an event or a delegate is invoked and not when it is assigned.</span></span>
  
- <span data-ttu-id="6a2a2-109">Un constructeur statique ne peut pas être appelé directement.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-109">A static constructor cannot be called directly.</span></span>  
  
- <span data-ttu-id="6a2a2-110">L’utilisateur n’a aucun contrôle sur le moment d’exécution du constructeur statique dans le programme.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-110">The user has no control on when the static constructor is executed in the program.</span></span>  
  
- <span data-ttu-id="6a2a2-111">Généralement, on utilise des constructeurs statiques quand la classe utilise un fichier journal et que le constructeur sert à écrire des entrées dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-111">A typical use of static constructors is when the class is using a log file and the constructor is used to write entries to this file.</span></span>  
  
- <span data-ttu-id="6a2a2-112">Les constructeurs statiques sont également utiles pour la création de classes wrapper pour du code non managé, quand le constructeur peut appeler la méthode `LoadLibrary`.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-112">Static constructors are also useful when creating wrapper classes for unmanaged code, when the constructor can call the `LoadLibrary` method.</span></span>  
  
- <span data-ttu-id="6a2a2-113">Si un constructeur statique lève une exception, le runtime ne l’appelle pas une deuxième fois et le type reste non initialisé pour la durée de vie du domaine d’application dans lequel votre programme s’exécute.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-113">If a static constructor throws an exception, the runtime will not invoke it a second time, and the type will remain uninitialized for the lifetime of the application domain in which your program is running.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a2a2-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="6a2a2-114">Example</span></span>  
 <span data-ttu-id="6a2a2-115">Dans cet exemple, la classe `Bus` possède un constructeur statique.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-115">In this example, class `Bus` has a static constructor.</span></span> <span data-ttu-id="6a2a2-116">Quand la première instance de `Bus` est créée (`bus1`), le constructeur statique est appelé pour initialiser la classe.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-116">When the first instance of `Bus` is created (`bus1`), the static constructor is invoked to initialize the class.</span></span> <span data-ttu-id="6a2a2-117">L’exemple de sortie vérifie que le constructeur statique s’exécute une seule fois, même si deux instances de `Bus` sont créées, et qu’il s’exécute avant le constructeur d’instance.</span><span class="sxs-lookup"><span data-stu-id="6a2a2-117">The sample output verifies that the static constructor runs only one time, even though two instances of `Bus` are created, and that it runs before the instance constructor runs.</span></span>  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]  
  
## <a name="see-also"></a><span data-ttu-id="6a2a2-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a2a2-118">See also</span></span>

- [<span data-ttu-id="6a2a2-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6a2a2-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6a2a2-120">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="6a2a2-120">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="6a2a2-121">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="6a2a2-121">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="6a2a2-122">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="6a2a2-122">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="6a2a2-123">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="6a2a2-123">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
