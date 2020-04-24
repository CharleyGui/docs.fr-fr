---
title: Instructions d’utilisation de la mémoire<T> et de l’étendue<T>
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 1f0d513e8bfd1668ee548315597385c555d374ef
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135774"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="c524a-102">Instructions d’utilisation de Memory\<T> et de Span\<T></span><span class="sxs-lookup"><span data-stu-id="c524a-102">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="c524a-103">.NET Core inclut un nombre de types qui représentent une région contiguë arbitraire de mémoire.</span><span class="sxs-lookup"><span data-stu-id="c524a-103">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="c524a-104">.NET Core 2.0 a introduit <xref:System.Span%601> et <xref:System.ReadOnlySpan%601>, qui sont des mémoires tampons légères pouvant être sauvegardées par de la mémoire managée ou non managée.</span><span class="sxs-lookup"><span data-stu-id="c524a-104">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="c524a-105">Ces types pouvant uniquement être stockés sur la pile, ils sont ne sont pas adaptés à plusieurs scénarios, notamment les appels de méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="c524a-105">Because these types can only be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="c524a-106">.NET Core 2.1 ajoute un certain nombre de types supplémentaires, notamment <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601> et <xref:System.Buffers.MemoryPool%601>.</span><span class="sxs-lookup"><span data-stu-id="c524a-106">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="c524a-107">Comme <xref:System.Span%601>, <xref:System.Memory%601> et ses types associés peuvent être sauvegardés par la mémoire managée et non managée.</span><span class="sxs-lookup"><span data-stu-id="c524a-107">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="c524a-108">Contrairement à <xref:System.Span%601>, <xref:System.Memory%601> peut être stockée sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="c524a-108">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can be stored on the managed heap.</span></span>

<span data-ttu-id="c524a-109"><xref:System.Span%601> et <xref:System.Memory%601> sont des mémoires tampons de données structurées qui peuvent être utilisées dans les pipelines.</span><span class="sxs-lookup"><span data-stu-id="c524a-109">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="c524a-110">Autrement dit, elles sont conçues afin que certaines données ou leur totalité puissent être transmises efficacement à des composants du pipeline qui puissent les traiter et, éventuellement, modifier la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-110">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="c524a-111">Étant donné que <xref:System.Memory%601> et ses types associés sont accessibles par plusieurs composants ou par plusieurs threads, il est important que les développeurs suivent des instructions d’utilisation standard pour produire un code robuste.</span><span class="sxs-lookup"><span data-stu-id="c524a-111">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="c524a-112">Gestion des propriétaires, des consommateurs et de la durée de vie</span><span class="sxs-lookup"><span data-stu-id="c524a-112">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="c524a-113">Les mémoires tampons pouvant passer d’une API à l’autre et étant parfois accessibles depuis plusieurs threads, il est important de tenir compte de la gestion de la durée de vie.</span><span class="sxs-lookup"><span data-stu-id="c524a-113">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="c524a-114">Il y a trois concepts fondamentaux :</span><span class="sxs-lookup"><span data-stu-id="c524a-114">There are three core concepts:</span></span>

- <span data-ttu-id="c524a-115">**Propriété**.</span><span class="sxs-lookup"><span data-stu-id="c524a-115">**Ownership**.</span></span> <span data-ttu-id="c524a-116">Le propriétaire d’une instance de la mémoire tampon est responsable de la gestion de la durée de vie, notamment de la destruction de la mémoire tampon lorsqu’elle n’est plus utilisée.</span><span class="sxs-lookup"><span data-stu-id="c524a-116">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="c524a-117">Toutes les mémoires tampons ont un propriétaire unique.</span><span class="sxs-lookup"><span data-stu-id="c524a-117">All buffers have a single owner.</span></span> <span data-ttu-id="c524a-118">En règle générale, le propriétaire est le composant qui a créé la mémoire tampon ou l’a reçue à partir d’une fabrique.</span><span class="sxs-lookup"><span data-stu-id="c524a-118">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="c524a-119">La propriété peut également être transférée ; **Component-A** peut abandonner le contrôle de la mémoire tampon à **Component-B**, à la suite de quoi **Component-A** ne peut plus utiliser la mémoire tampon, et \*\*Component-B \*\* devient responsable de sa destruction lorsqu’elle n’est plus utilisée.</span><span class="sxs-lookup"><span data-stu-id="c524a-119">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="c524a-120">**Consommation**.</span><span class="sxs-lookup"><span data-stu-id="c524a-120">**Consumption**.</span></span> <span data-ttu-id="c524a-121">Le consommateur d’une instance de la mémoire tampon est autorisé à utiliser l’instance de la mémoire tampon en la lisant et, éventuellement, en écrivant dedans.</span><span class="sxs-lookup"><span data-stu-id="c524a-121">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="c524a-122">Les mémoires tampons peuvent avoir un consommateur à la fois, sauf si un mécanisme de synchronisation externe est disponible.</span><span class="sxs-lookup"><span data-stu-id="c524a-122">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="c524a-123">Notez que le consommateur actif d’une mémoire tampon n’est pas nécessairement son propriétaire.</span><span class="sxs-lookup"><span data-stu-id="c524a-123">Note that the active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="c524a-124">**Bail**.</span><span class="sxs-lookup"><span data-stu-id="c524a-124">**Lease**.</span></span> <span data-ttu-id="c524a-125">Le bail est la durée pendant laquelle un composant particulier est autorisé à être le consommateur de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-125">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="c524a-126">L'exemple de pseudo-code suivant illustre ces trois concepts.</span><span class="sxs-lookup"><span data-stu-id="c524a-126">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="c524a-127">Il inclut une méthode `Main` qui instancie une mémoire tampon <xref:System.Memory%601> de type <xref:System.Char> et appelle la méthode `WriteInt32ToBuffer` pour écrire la représentation sous forme de chaîne d’un entier dans la mémoire tampon, puis la méthode `DisplayBufferToConsole` pour afficher la valeur de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-127">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

```csharp
using System;

class Program
{
    // Write 'value' as a human-readable string to the output buffer.
    void WriteInt32ToBuffer(int value, Buffer buffer);

    // Display the contents of the buffer to the console.
    void DisplayBufferToConsole(Buffer buffer);

    // Application code
    static void Main()
    {
        var buffer = CreateBuffer();
        try
        {
            int value = Int32.Parse(Console.ReadLine());
            WriteInt32ToBuffer(value, buffer);
            DisplayBufferToConsole(buffer);
        }
        finally
        {
            buffer.Destroy();
        }
    }
}
```

<span data-ttu-id="c524a-128">La méthode `Main` crée la mémoire tampon (dans ce cas une instance <xref:System.Span%601>) et est donc son propriétaire.</span><span class="sxs-lookup"><span data-stu-id="c524a-128">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="c524a-129">Pour cette raison, `Main` est responsable de la destruction de la mémoire tampon lorsqu’elle n’est plus utilisée.</span><span class="sxs-lookup"><span data-stu-id="c524a-129">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="c524a-130">Elle est effectuée en appelant la méthode <xref:System.Span%601.Clear?displayProperty=nameWithType> de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-130">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c524a-131">(Ici, la méthode <xref:System.Span%601.Clear> efface effectivement la mémoire de la mémoire tampon ; la structure <xref:System.Span%601> n’a pas vraiment de méthode de destruction de la mémoire tampon.)</span><span class="sxs-lookup"><span data-stu-id="c524a-131">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="c524a-132">La mémoire tampon a deux consommateurs, à savoir `WriteInt32ToBuffer` et `DisplayBufferToConsole`.</span><span class="sxs-lookup"><span data-stu-id="c524a-132">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="c524a-133">Il n'y a qu’un seul consommateur à la fois (d’abord `WriteInt32ToBuffer`, puis `DisplayBufferToConsole`), et aucune des consommateurs ne possède la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-133">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="c524a-134">Notez également que « consommateur » dans ce contexte n’implique pas une vue en lecture seule de la mémoire tampon ; comme `WriteInt32ToBuffer`, les consommateurs peuvent modifier le contenu de la mémoire tampon s’ils disposent d’une vue en lecture/écriture de cette dernière.</span><span class="sxs-lookup"><span data-stu-id="c524a-134">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="c524a-135">La méthode `WriteInt32ToBuffer` a un bail pour la mémoire tampon (peut consommer) entre le début de l’appel de méthode et le moment du retour de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c524a-135">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="c524a-136">De même, `DisplayBufferToConsole` a un bail pour la mémoire tampon pendant son exécution et en est libéré lorsque la méthode se déroule.</span><span class="sxs-lookup"><span data-stu-id="c524a-136">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="c524a-137">(Il n’existe aucune API pour la gestion de bail ; un « bail » est un concept.)</span><span class="sxs-lookup"><span data-stu-id="c524a-137">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="c524a-138">Memory\<T> et le modèle propriétaire/consommateur</span><span class="sxs-lookup"><span data-stu-id="c524a-138">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="c524a-139">Comme mentionné dans la section [Propriétaires, consommateurs et gestion de la durée de vie](#owners-consumers-and-lifetime-management), une mémoire tampon a toujours un propriétaire.</span><span class="sxs-lookup"><span data-stu-id="c524a-139">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="c524a-140">.NET Core prend en charge deux modèles de propriété :</span><span class="sxs-lookup"><span data-stu-id="c524a-140">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="c524a-141">Un modèle qui prend en charge la propriété unique.</span><span class="sxs-lookup"><span data-stu-id="c524a-141">A model that supports single ownership.</span></span> <span data-ttu-id="c524a-142">Une mémoire tampon a un propriétaire unique pour toute sa durée de vie.</span><span class="sxs-lookup"><span data-stu-id="c524a-142">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="c524a-143">Un modèle qui prend en charge le transfert de propriété.</span><span class="sxs-lookup"><span data-stu-id="c524a-143">A model that supports ownership transfer.</span></span> <span data-ttu-id="c524a-144">La propriété d’une mémoire tampon peut être transférée de son propriétaire d’origine (son créateur) à un autre composant, qui devient alors responsable de la gestion de la durée de vie de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-144">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="c524a-145">Ce propriétaire peut à son tour transférer la propriété à un autre composant, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="c524a-145">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="c524a-146">Vous utilisez l’interface <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> pour gérer explicitement la propriété d’une mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-146">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="c524a-147"><xref:System.Buffers.IMemoryOwner%601> prend en charge les deux modèles de propriété.</span><span class="sxs-lookup"><span data-stu-id="c524a-147"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="c524a-148">Le composant qui a une référence <xref:System.Buffers.IMemoryOwner%601> possède la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-148">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="c524a-149">L’exemple suivant utilise une instance <xref:System.Buffers.IMemoryOwner%601?> pour refléter la propriété d’une mémoire tampon <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="c524a-149">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of an <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="c524a-150">Nous pouvons également écrire cet exemple avec [`using`](../../csharp/language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="c524a-150">We can also write this example with the [`using`](../../csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="c524a-151">Dans ce code :</span><span class="sxs-lookup"><span data-stu-id="c524a-151">In this code:</span></span>

- <span data-ttu-id="c524a-152">La méthode `Main` conserve la référence à l’instance <xref:System.Buffers.IMemoryOwner%601>, donc la méthode `Main` est propriétaire de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-152">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="c524a-153">Les méthodes `WriteInt32ToBuffer` et `DisplayBufferToConsole` acceptent <xref:System.Memory%601> comme API publique.</span><span class="sxs-lookup"><span data-stu-id="c524a-153">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="c524a-154">Par conséquent, il y a des consommateurs de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-154">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="c524a-155">Et ils ne la consomment qu’un par un.</span><span class="sxs-lookup"><span data-stu-id="c524a-155">And they only consume it one at a time.</span></span>

<span data-ttu-id="c524a-156">Bien que la méthode `WriteInt32ToBuffer` soit destinée à écrire une valeur dans la mémoire tampon, ce n’est pas le cas pour la méthode `DisplayBufferToConsole`.</span><span class="sxs-lookup"><span data-stu-id="c524a-156">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="c524a-157">Pour refléter cette modification, un argument de type <xref:System.ReadOnlyMemory%601> peut avoir été accepté.</span><span class="sxs-lookup"><span data-stu-id="c524a-157">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="c524a-158">Pour plus d’informations <xref:System.ReadOnlyMemory%601>sur, consultez [#2 de règles :\<utilisez ReadOnlySpan t>\<ou ReadOnlyMemory t> si la mémoire tampon doit être en lecture seule](#rule-2).</span><span class="sxs-lookup"><span data-stu-id="c524a-158">For additional information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="c524a-159">Instances Memory\<T> « sans propriétaire »</span><span class="sxs-lookup"><span data-stu-id="c524a-159">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="c524a-160">Vous pouvez créer une instance <xref:System.Memory%601> sans utiliser <xref:System.Buffers.IMemoryOwner%601>.</span><span class="sxs-lookup"><span data-stu-id="c524a-160">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="c524a-161">Dans ce cas, la propriété de la mémoire tampon est implicite plutôt qu’explicite et seul le modèle de propriétaire unique est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c524a-161">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="c524a-162">Pour ce faire, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="c524a-162">You can do this by:</span></span>

- <span data-ttu-id="c524a-163">appeler directement l’un des constructeurs <xref:System.Memory%601> en passant à un `T[]`, comme dans l’exemple suivant ;</span><span class="sxs-lookup"><span data-stu-id="c524a-163">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="c524a-164">appeler la méthode d'extension [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) pour produire une instance `ReadOnlyMemory<char>`.</span><span class="sxs-lookup"><span data-stu-id="c524a-164">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="c524a-165">La méthode qui crée initialement l’instance <xref:System.Memory%601> est le propriétaire implicite de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-165">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="c524a-166">La propriété ne peut pas être transférée à n’importe quel autre composant, car il n’y a pas d’instance <xref:System.Buffers.IMemoryOwner%601> pour faciliter le transfert.</span><span class="sxs-lookup"><span data-stu-id="c524a-166">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="c524a-167">(Comme alternative, vous pouvez également imaginer que le récupérateur de mémoire du runtime possède la mémoire tampon et que toutes les méthodes ne fassent que consommer la mémoire tampon.)</span><span class="sxs-lookup"><span data-stu-id="c524a-167">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="c524a-168">Indications relatives à l'utilisation</span><span class="sxs-lookup"><span data-stu-id="c524a-168">Usage guidelines</span></span>

<span data-ttu-id="c524a-169">Un bloc de mémoire étant une propriété, mais destiné à être transmis vers plusieurs composants dont certains peuvent fonctionner simultanément sur un bloc de mémoire particulier, il est important de définir des instructions pour l’utilisation de <xref:System.Memory%601> et de <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="c524a-169">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="c524a-170">Des instructions sont nécessaires pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="c524a-170">Guidelines are necessary because:</span></span>

- <span data-ttu-id="c524a-171">Il est possible qu’un composant conserve une référence à un bloc de mémoire une fois que son propriétaire l’a libéré.</span><span class="sxs-lookup"><span data-stu-id="c524a-171">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="c524a-172">Il est possible qu’un composant fonctionne sur une mémoire tampon en même temps qu’un autre composant et que ce processus endommage les données de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-172">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="c524a-173">Alors que l’allocation par pile de <xref:System.Span%601> optimise les performances et fait de <xref:System.Span%601> le type préféré de fonctionnement sur un bloc de mémoire, elle soumet également <xref:System.Span%601> à certaines restrictions majeures.</span><span class="sxs-lookup"><span data-stu-id="c524a-173">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="c524a-174">Il est important de savoir quand utiliser un <xref:System.Span%601> et quand utiliser <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="c524a-174">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="c524a-175">Voici nos recommandations quant à l’utilisation réussie de <xref:System.Memory%601> et de ses types associés.</span><span class="sxs-lookup"><span data-stu-id="c524a-175">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="c524a-176">Notez que les conseils concernant <xref:System.Memory%601> et <xref:System.Span%601> s’appliquent également à <xref:System.ReadOnlyMemory%601> et à <xref:System.ReadOnlySpan%601>, sauf si c’est explicitement exclu.</span><span class="sxs-lookup"><span data-stu-id="c524a-176">Note that guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="c524a-177">**#1 de règle : pour une API synchrone, utilisez\<Span t> au lieu\<de Memory t> en tant que paramètre, si possible.**</span><span class="sxs-lookup"><span data-stu-id="c524a-177">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="c524a-178"><xref:System.Span%601> est plus polyvalente que <xref:System.Memory%601> et peut représenter une plus grande variété de mémoires tampons contiguës.</span><span class="sxs-lookup"><span data-stu-id="c524a-178"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="c524a-179"><xref:System.Span%601> offre également de meilleures performances que <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="c524a-179"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="c524a-180">Enfin, vous pouvez utiliser la propriété <xref:System.Memory%601.Span?displayProperty=nameWithType> pour convertir une instance <xref:System.Memory%601> en <xref:System.Span%601>, bien que la conversion Span\<T >- to-Memory\<T > ne soit pas possible.</span><span class="sxs-lookup"><span data-stu-id="c524a-180">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="c524a-181">Par conséquent, si vos appelants ont une instance <xref:System.Memory%601>, ils pourront de toute façon appeler vos méthodes avec des paramètres <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="c524a-181">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="c524a-182">L’utilisation d’un paramètre de type <xref:System.Span%601> au lieu d’un paramètre de type <xref:System.Memory%601> vous aide également à écrire une implémentation correcte de la méthode de consommation.</span><span class="sxs-lookup"><span data-stu-id="c524a-182">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="c524a-183">Des vérifications automatiques au moment de la compilation vous permettent de garantir que vous ne tentez pas d’accéder à la mémoire tampon au-delà de votre bail de méthode (nous y reviendrons plus tard).</span><span class="sxs-lookup"><span data-stu-id="c524a-183">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="c524a-184">Vous devrez parfois utiliser un paramètre <xref:System.Memory%601> au lieu d’un paramètre <xref:System.Span%601>, même si vous êtes entièrement synchrone.</span><span class="sxs-lookup"><span data-stu-id="c524a-184">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="c524a-185">Il est possible qu’une API dont vous dépendez n’accepte que des arguments <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="c524a-185">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="c524a-186">C’est bien, mais tenez compte des compromis impliqués par l’utilisation synchrone de <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="c524a-186">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="c524a-187">**#2 de règle : utilisez\<ReadOnlySpan t> ou\<ReadOnlyMemory t> si la mémoire tampon doit être en lecture seule.**</span><span class="sxs-lookup"><span data-stu-id="c524a-187">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="c524a-188">Dans les exemples précédents, la méthode `DisplayBufferToConsole` lit uniquement à partir de la mémoire tampon ; elle ne modifie pas le contenu de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c524a-188">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="c524a-189">La signature de méthode doit être modifiée comme suit.</span><span class="sxs-lookup"><span data-stu-id="c524a-189">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="c524a-190">En fait, si nous combinons cette règle et la règle 1, nous pouvons faire encore mieux et réécrire la signature de méthode comme suit :</span><span class="sxs-lookup"><span data-stu-id="c524a-190">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="c524a-191">La méthode `DisplayBufferToConsole` fonctionne désormais avec pratiquement chaque type de mémoire tampon imaginable : `T[]`, stockage alloué avec [stackalloc](../../csharp/language-reference/operators/stackalloc.md), et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="c524a-191">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), and so on.</span></span> <span data-ttu-id="c524a-192">Vous pouvez même y passer directement une chaîne <xref:System.String> !</span><span class="sxs-lookup"><span data-stu-id="c524a-192">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="c524a-193">**#3 de règle : Si votre méthode accepte\<la mémoire t> `void`et retourne, vous ne devez pas\<utiliser l’instance Memory t> après le retour de la méthode.**</span><span class="sxs-lookup"><span data-stu-id="c524a-193">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="c524a-194">Ceci est lié au concept de « bail » mentionné précédemment.</span><span class="sxs-lookup"><span data-stu-id="c524a-194">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="c524a-195">Un bail de méthode avec renvoi d’annulation sur l’instance <xref:System.Memory%601> commence lorsqu’on entre dans la méthode et se termine lorsqu’on la quitte.</span><span class="sxs-lookup"><span data-stu-id="c524a-195">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="c524a-196">Prenons l’exemple suivant, qui appelle `Log` dans une boucle basée sur l’entrée à partir de la console.</span><span class="sxs-lookup"><span data-stu-id="c524a-196">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="c524a-197">Si `Log` est une méthode parfaitement synchrone, ce code se comporte comme prévu, car il n’y a qu’un seul consommateur actif de l’instance de la mémoire à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="c524a-197">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="c524a-198">Mais imaginez plutôt que `Log` a cette implémentation.</span><span class="sxs-lookup"><span data-stu-id="c524a-198">But imagine instead that `Log` has this implementation.</span></span>

```csharp
// !!! INCORRECT IMPLEMENTATION !!!
static void Log(ReadOnlyMemory<char> message)
{
    // Run in background so that we don't block the main thread while performing IO.
    Task.Run(() =>
    {
        StreamWriter sw = File.AppendText(@".\input-numbers.dat");
        sw.WriteLine(message);
    });
}
```

<span data-ttu-id="c524a-199">Dans cette implémentation, `Log` enfreint son bail, car il tente toujours d’utiliser l’instance <xref:System.Memory%601> en arrière-plan après le retour de la méthode d’origine.</span><span class="sxs-lookup"><span data-stu-id="c524a-199">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="c524a-200">La méthode `Main` pourrait muter la mémoire tampon pendant que `Log` tente de la lire, ce qui pourrait entraîner une altération des données.</span><span class="sxs-lookup"><span data-stu-id="c524a-200">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="c524a-201">Il y a de nombreuses manières de résoudre ce problème :</span><span class="sxs-lookup"><span data-stu-id="c524a-201">There are several ways to resolve this:</span></span>

- <span data-ttu-id="c524a-202">La méthode `Log` peut retourner une <xref:System.Threading.Tasks.Task> au lieu de `void`, comme le fait l’implémentation suivante de la méthode `Log`.</span><span class="sxs-lookup"><span data-stu-id="c524a-202">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="c524a-203">À la place, `Log` peut plutôt être implémenté comme suit :</span><span class="sxs-lookup"><span data-stu-id="c524a-203">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="c524a-204">**#4 de règle : Si votre méthode accepte une\<> de mémoire t et retourne une tâche, vous ne devez pas\<utiliser l’instance de mémoire t> une fois que la tâche est passée à un état terminal.**</span><span class="sxs-lookup"><span data-stu-id="c524a-204">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="c524a-205">Il s’agit simplement la variante asynchrone de la règle 3.</span><span class="sxs-lookup"><span data-stu-id="c524a-205">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="c524a-206">La méthode `Log` de l’exemple précédent peut être écrite comme suit pour se conformer à cette règle :</span><span class="sxs-lookup"><span data-stu-id="c524a-206">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="c524a-207">Ici, « état terminal » signifie que la tâche passe à un état terminé, ayant généré une erreur ou annulé.</span><span class="sxs-lookup"><span data-stu-id="c524a-207">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="c524a-208">En d’autres termes, « état terminal » signifie « tout ce qui provoquerait une attente lors du lancement ou de la poursuite de l’exécution. »</span><span class="sxs-lookup"><span data-stu-id="c524a-208">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="c524a-209">Ces conseils s’appliquent aux méthodes qui retournent <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, ou n’importe quel type similaire.</span><span class="sxs-lookup"><span data-stu-id="c524a-209">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="c524a-210">**#5 de règle : Si votre constructeur accepte\<la mémoire T> en tant que paramètre, les méthodes d’instance sur l’objet construit sont supposées\<être des consommateurs de l’instance de la mémoire t>.**</span><span class="sxs-lookup"><span data-stu-id="c524a-210">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="c524a-211">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="c524a-211">Consider the following example:</span></span>

```csharp
class OddValueExtractor
{
    public OddValueExtractor(ReadOnlyMemory<int> input);
    public bool TryReadNextOddValue(out int value);
}

void PrintAllOddValues(ReadOnlyMemory<int> input)
{
    var extractor = new OddValueExtractor(input);
    while (extractor.TryReadNextOddValue(out int value))
    {
      Console.WriteLine(value);
    }
}
```

<span data-ttu-id="c524a-212">Ici, le constructeur`OddValueExtractor` accepte `ReadOnlyMemory<int>` comme paramètre de constructeur, si bien que le constructeur lui-même est un consommateur de l’instance `ReadOnlyMemory<int>` et que toutes les méthodes d’instance sur la valeur retournée sont également des consommateurs de l’instance `ReadOnlyMemory<int>` d’origine.</span><span class="sxs-lookup"><span data-stu-id="c524a-212">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="c524a-213">Cela signifie que `TryReadNextOddValue` consomme l’instance `ReadOnlyMemory<int>`, même si l’instance n’est pas passée directement à la méthode `TryReadNextOddValue`.</span><span class="sxs-lookup"><span data-stu-id="c524a-213">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="c524a-214">**#6 de règle : Si vous disposez d’une\<propriété de type mémoire t> définissable (ou d’une méthode d’instance équivalente) sur votre type, les méthodes d’instance sur cet objet sont\<supposées être des consommateurs de l’instance de la mémoire T>.**</span><span class="sxs-lookup"><span data-stu-id="c524a-214">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="c524a-215">Il s’agit simplement d’une variante de la règle 5.</span><span class="sxs-lookup"><span data-stu-id="c524a-215">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="c524a-216">Cette règle existe, car les setters de propriété ou les méthodes équivalentes sont supposés capturer et conserver leurs entrées, de manière que les méthodes d’instances sur le même objet puissent utiliser l’état de capture.</span><span class="sxs-lookup"><span data-stu-id="c524a-216">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="c524a-217">L'exemple suivant déclenche cette règle :</span><span class="sxs-lookup"><span data-stu-id="c524a-217">The following example triggers this rule:</span></span>

```csharp
class Person
{
    // Settable property.
    public Memory<char> FirstName { get; set; }

    // alternatively, equivalent "setter" method
    public SetFirstName(Memory<char> value);

    // alternatively, a public settable field
    public Memory<char> FirstName;
}
```

<span data-ttu-id="c524a-218">**#7 de règle : Si vous avez une\<référence IMemoryOwner T>, vous devez à un moment l’éliminer ou transférer sa propriété (mais pas les deux).**</span><span class="sxs-lookup"><span data-stu-id="c524a-218">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="c524a-219">Dans la mesure où une instance <xref:System.Memory%601> peut être sauvegardée par de la mémoire, managée ou non, le propriétaire doit appeler <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> lorsque le travail effectué sur l’instance <xref:System.Memory%601> est terminé.</span><span class="sxs-lookup"><span data-stu-id="c524a-219">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="c524a-220">Le propriétaire peut également transférer la propriété de l’instance <xref:System.Buffers.IMemoryOwner%601> à un autre composant. Le composant d’acquisition devient alors responsable de l’appel de <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> au moment opportun (nous y reviendrons plus tard).</span><span class="sxs-lookup"><span data-stu-id="c524a-220">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="c524a-221">Ne pas appeler la méthode <xref:System.Buffers.MemoryPool%601.Dispose%2A> peut entraîner des fuites de mémoire non managée ou une autre dégradation des performances.</span><span class="sxs-lookup"><span data-stu-id="c524a-221">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="c524a-222">Cette règle s’applique également au code qui appelle les méthodes de fabrique, telles que <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c524a-222">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c524a-223">L’appelant devient le propriétaire du <xref:System.Buffers.IMemoryOwner%601> retourné et est responsable de la suppression de l’instance terminée.</span><span class="sxs-lookup"><span data-stu-id="c524a-223">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="c524a-224">**#8 de règle : Si vous avez un\<paramètre IMemoryOwner T> dans la surface de l’API, vous acceptez la propriété de cette instance.**</span><span class="sxs-lookup"><span data-stu-id="c524a-224">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="c524a-225">Accepter une instance de ce type signale que votre composant a l’intention de prendre possession de cette instance.</span><span class="sxs-lookup"><span data-stu-id="c524a-225">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="c524a-226">Votre composant devient responsable de la suppression correcte conformément à la règle 7.</span><span class="sxs-lookup"><span data-stu-id="c524a-226">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="c524a-227">Tout composant qui transfère la propriété de l’instance <xref:System.Buffers.IMemoryOwner%601> à un autre composant ne doit plus utiliser cette instance lorsque l’appel de méthode se termine.</span><span class="sxs-lookup"><span data-stu-id="c524a-227">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c524a-228">Si votre constructeur accepte <xref:System.Buffers.IMemoryOwner%601> comme paramètre, son type doit implémenter <xref:System.IDisposable> et votre méthode <xref:System.IDisposable.Dispose%2A> doit appeler <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c524a-228">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c524a-229">**#9 de règle : Si vous encapsulez une méthode p/Invoke synchrone, votre API doit\<accepter l’étendue T> en tant que paramètre.**</span><span class="sxs-lookup"><span data-stu-id="c524a-229">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="c524a-230">Conformément à la règle 1, <xref:System.Span%601> est généralement le type correct à utiliser pour les API synchrones.</span><span class="sxs-lookup"><span data-stu-id="c524a-230">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="c524a-231">Vous pouvez épingler des instances <xref:System.Span%601> via le mot clé [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) mot clé, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c524a-231">You can pin <xref:System.Span%601> instances via the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

```csharp
using System.Runtime.InteropServices;

[DllImport(...)]
private static extern unsafe int ExportedMethod(byte* pbData, int cbData);

public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        int retVal = ExportedMethod(pbData, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

<span data-ttu-id="c524a-232">Dans l’exemple précédent, `pbData` peut être Null si, par exemple, l’étendue d’entrée est vide.</span><span class="sxs-lookup"><span data-stu-id="c524a-232">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="c524a-233">Si la méthode exportée requiert absolument que `pbData` soit non Null, même si `cbData` est égal à 0, la méthode peut être implémentée comme suit :</span><span class="sxs-lookup"><span data-stu-id="c524a-233">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

```csharp
public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        byte dummy = 0;
        int retVal = ExportedMethod((pbData != null) ? pbData : &dummy, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

<span data-ttu-id="c524a-234">**#10 de règle : Si vous encapsulez une méthode p/Invoke asynchrone, votre API doit\<accepter la mémoire T> en tant que paramètre.**</span><span class="sxs-lookup"><span data-stu-id="c524a-234">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="c524a-235">Étant donné que vous ne [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) pouvez pas utiliser le mot clé dans les <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> opérations asynchrones <xref:System.Memory%601> , vous utilisez la méthode pour épingler des instances, quel que soit le type de mémoire contiguë représenté par l’instance.</span><span class="sxs-lookup"><span data-stu-id="c524a-235">Since you cannot use the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="c524a-236">L’exemple suivant montre comment utiliser cette API pour effectuer un appel p/invoke asynchrone.</span><span class="sxs-lookup"><span data-stu-id="c524a-236">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

```csharp
using System.Runtime.InteropServices;

[UnmanagedFunctionPointer(...)]
private delegate void OnCompletedCallback(IntPtr state, int result);

[DllImport(...)]
private static extern unsafe int ExportedAsyncMethod(byte* pbData, int cbData, IntPtr pState, IntPtr lpfnOnCompletedCallback);

private static readonly IntPtr _callbackPtr = GetCompletionCallbackPointer();

public unsafe Task<int> ManagedWrapperAsync(Memory<byte> data)
{
    // setup
    var tcs = new TaskCompletionSource<int>();
    var state = new MyCompletedCallbackState
    {
        Tcs = tcs
    };
    var pState = (IntPtr)GCHandle.Alloc(state);

    var memoryHandle = data.Pin();
    state.MemoryHandle = memoryHandle;

    // make the call
    int result;
    try
    {
        result = ExportedAsyncMethod((byte*)memoryHandle.Pointer, data.Length, pState, _callbackPtr);
    }
    catch
    {
        ((GCHandle)pState).Free(); // cleanup since callback won't be invoked
        memoryHandle.Dispose();
        throw;
    }

    if (result != PENDING)
    {
        // Operation completed synchronously; invoke callback manually
        // for result processing and cleanup.
        MyCompletedCallbackImplementation(pState, result);
    }

    return tcs.Task;
}

private static void MyCompletedCallbackImplementation(IntPtr state, int result)
{
    GCHandle handle = (GCHandle)state;
    var actualState = (MyCompletedCallbackState)(handle.Target);
    handle.Free();
    actualState.MemoryHandle.Dispose();

    /* error checking result goes here */

    if (error)
    {
        actualState.Tcs.SetException(...);
    }
    else
    {
        actualState.Tcs.SetResult(result);
    }
}

private static IntPtr GetCompletionCallbackPointer()
{
    OnCompletedCallback callback = MyCompletedCallbackImplementation;
    GCHandle.Alloc(callback); // keep alive for lifetime of application
    return Marshal.GetFunctionPointerForDelegate(callback);
}

private class MyCompletedCallbackState
{
    public TaskCompletionSource<int> Tcs;
    public MemoryHandle MemoryHandle;
}
```

## <a name="see-also"></a><span data-ttu-id="c524a-237">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c524a-237">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
