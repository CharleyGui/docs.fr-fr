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
# <a name="memoryt-and-spant-usage-guidelines"></a>Instructions d’utilisation de Memory\<T> et de Span\<T>

.NET Core inclut un nombre de types qui représentent une région contiguë arbitraire de mémoire. .NET Core 2.0 a introduit <xref:System.Span%601> et <xref:System.ReadOnlySpan%601>, qui sont des mémoires tampons légères pouvant être sauvegardées par de la mémoire managée ou non managée. Ces types pouvant uniquement être stockés sur la pile, ils sont ne sont pas adaptés à plusieurs scénarios, notamment les appels de méthode asynchrone. .NET Core 2.1 ajoute un certain nombre de types supplémentaires, notamment <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601> et <xref:System.Buffers.MemoryPool%601>. Comme <xref:System.Span%601>, <xref:System.Memory%601> et ses types associés peuvent être sauvegardés par la mémoire managée et non managée. Contrairement à <xref:System.Span%601>, <xref:System.Memory%601> peut être stockée sur le tas managé.

<xref:System.Span%601> et <xref:System.Memory%601> sont des mémoires tampons de données structurées qui peuvent être utilisées dans les pipelines. Autrement dit, elles sont conçues afin que certaines données ou leur totalité puissent être transmises efficacement à des composants du pipeline qui puissent les traiter et, éventuellement, modifier la mémoire tampon. Étant donné que <xref:System.Memory%601> et ses types associés sont accessibles par plusieurs composants ou par plusieurs threads, il est important que les développeurs suivent des instructions d’utilisation standard pour produire un code robuste.

## <a name="owners-consumers-and-lifetime-management"></a>Gestion des propriétaires, des consommateurs et de la durée de vie

Les mémoires tampons pouvant passer d’une API à l’autre et étant parfois accessibles depuis plusieurs threads, il est important de tenir compte de la gestion de la durée de vie. Il y a trois concepts fondamentaux :

- **Propriété**. Le propriétaire d’une instance de la mémoire tampon est responsable de la gestion de la durée de vie, notamment de la destruction de la mémoire tampon lorsqu’elle n’est plus utilisée. Toutes les mémoires tampons ont un propriétaire unique. En règle générale, le propriétaire est le composant qui a créé la mémoire tampon ou l’a reçue à partir d’une fabrique. La propriété peut également être transférée ; **Component-A** peut abandonner le contrôle de la mémoire tampon à **Component-B**, à la suite de quoi **Component-A** ne peut plus utiliser la mémoire tampon, et **Component-B ** devient responsable de sa destruction lorsqu’elle n’est plus utilisée.

- **Consommation**. Le consommateur d’une instance de la mémoire tampon est autorisé à utiliser l’instance de la mémoire tampon en la lisant et, éventuellement, en écrivant dedans. Les mémoires tampons peuvent avoir un consommateur à la fois, sauf si un mécanisme de synchronisation externe est disponible. Notez que le consommateur actif d’une mémoire tampon n’est pas nécessairement son propriétaire.

- **Bail**. Le bail est la durée pendant laquelle un composant particulier est autorisé à être le consommateur de la mémoire tampon.

L'exemple de pseudo-code suivant illustre ces trois concepts. Il inclut une méthode `Main` qui instancie une mémoire tampon <xref:System.Memory%601> de type <xref:System.Char> et appelle la méthode `WriteInt32ToBuffer` pour écrire la représentation sous forme de chaîne d’un entier dans la mémoire tampon, puis la méthode `DisplayBufferToConsole` pour afficher la valeur de la mémoire tampon.

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

La méthode `Main` crée la mémoire tampon (dans ce cas une instance <xref:System.Span%601>) et est donc son propriétaire. Pour cette raison, `Main` est responsable de la destruction de la mémoire tampon lorsqu’elle n’est plus utilisée. Elle est effectuée en appelant la méthode <xref:System.Span%601.Clear?displayProperty=nameWithType> de la mémoire tampon. (Ici, la méthode <xref:System.Span%601.Clear> efface effectivement la mémoire de la mémoire tampon ; la structure <xref:System.Span%601> n’a pas vraiment de méthode de destruction de la mémoire tampon.)

La mémoire tampon a deux consommateurs, à savoir `WriteInt32ToBuffer` et `DisplayBufferToConsole`. Il n'y a qu’un seul consommateur à la fois (d’abord `WriteInt32ToBuffer`, puis `DisplayBufferToConsole`), et aucune des consommateurs ne possède la mémoire tampon. Notez également que « consommateur » dans ce contexte n’implique pas une vue en lecture seule de la mémoire tampon ; comme `WriteInt32ToBuffer`, les consommateurs peuvent modifier le contenu de la mémoire tampon s’ils disposent d’une vue en lecture/écriture de cette dernière.

La méthode `WriteInt32ToBuffer` a un bail pour la mémoire tampon (peut consommer) entre le début de l’appel de méthode et le moment du retour de la méthode. De même, `DisplayBufferToConsole` a un bail pour la mémoire tampon pendant son exécution et en est libéré lorsque la méthode se déroule. (Il n’existe aucune API pour la gestion de bail ; un « bail » est un concept.)

## <a name="memoryt-and-the-ownerconsumer-model"></a>Memory\<T> et le modèle propriétaire/consommateur

Comme mentionné dans la section [Propriétaires, consommateurs et gestion de la durée de vie](#owners-consumers-and-lifetime-management), une mémoire tampon a toujours un propriétaire. .NET Core prend en charge deux modèles de propriété :

- Un modèle qui prend en charge la propriété unique. Une mémoire tampon a un propriétaire unique pour toute sa durée de vie.

- Un modèle qui prend en charge le transfert de propriété. La propriété d’une mémoire tampon peut être transférée de son propriétaire d’origine (son créateur) à un autre composant, qui devient alors responsable de la gestion de la durée de vie de la mémoire tampon. Ce propriétaire peut à son tour transférer la propriété à un autre composant, et ainsi de suite.

Vous utilisez l’interface <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> pour gérer explicitement la propriété d’une mémoire tampon. <xref:System.Buffers.IMemoryOwner%601> prend en charge les deux modèles de propriété. Le composant qui a une référence <xref:System.Buffers.IMemoryOwner%601> possède la mémoire tampon. L’exemple suivant utilise une instance <xref:System.Buffers.IMemoryOwner%601?> pour refléter la propriété d’une mémoire tampon <xref:System.Memory%601>.

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

Nous pouvons également écrire cet exemple avec [`using`](../../csharp/language-reference/keywords/using-statement.md):

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

Dans ce code :

- La méthode `Main` conserve la référence à l’instance <xref:System.Buffers.IMemoryOwner%601>, donc la méthode `Main` est propriétaire de la mémoire tampon.

- Les méthodes `WriteInt32ToBuffer` et `DisplayBufferToConsole` acceptent <xref:System.Memory%601> comme API publique. Par conséquent, il y a des consommateurs de la mémoire tampon. Et ils ne la consomment qu’un par un.

Bien que la méthode `WriteInt32ToBuffer` soit destinée à écrire une valeur dans la mémoire tampon, ce n’est pas le cas pour la méthode `DisplayBufferToConsole`. Pour refléter cette modification, un argument de type <xref:System.ReadOnlyMemory%601> peut avoir été accepté. Pour plus d’informations <xref:System.ReadOnlyMemory%601>sur, consultez [#2 de règles :\<utilisez ReadOnlySpan t>\<ou ReadOnlyMemory t> si la mémoire tampon doit être en lecture seule](#rule-2).

### <a name="ownerless-memoryt-instances"></a>Instances Memory\<T> « sans propriétaire »

Vous pouvez créer une instance <xref:System.Memory%601> sans utiliser <xref:System.Buffers.IMemoryOwner%601>. Dans ce cas, la propriété de la mémoire tampon est implicite plutôt qu’explicite et seul le modèle de propriétaire unique est pris en charge. Pour ce faire, vous pouvez :

- appeler directement l’un des constructeurs <xref:System.Memory%601> en passant à un `T[]`, comme dans l’exemple suivant ;

- appeler la méthode d'extension [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) pour produire une instance `ReadOnlyMemory<char>`.

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

La méthode qui crée initialement l’instance <xref:System.Memory%601> est le propriétaire implicite de la mémoire tampon. La propriété ne peut pas être transférée à n’importe quel autre composant, car il n’y a pas d’instance <xref:System.Buffers.IMemoryOwner%601> pour faciliter le transfert. (Comme alternative, vous pouvez également imaginer que le récupérateur de mémoire du runtime possède la mémoire tampon et que toutes les méthodes ne fassent que consommer la mémoire tampon.)

## <a name="usage-guidelines"></a>Indications relatives à l'utilisation

Un bloc de mémoire étant une propriété, mais destiné à être transmis vers plusieurs composants dont certains peuvent fonctionner simultanément sur un bloc de mémoire particulier, il est important de définir des instructions pour l’utilisation de <xref:System.Memory%601> et de <xref:System.Span%601>.  Des instructions sont nécessaires pour les raisons suivantes :

- Il est possible qu’un composant conserve une référence à un bloc de mémoire une fois que son propriétaire l’a libéré.

- Il est possible qu’un composant fonctionne sur une mémoire tampon en même temps qu’un autre composant et que ce processus endommage les données de la mémoire tampon.

- Alors que l’allocation par pile de <xref:System.Span%601> optimise les performances et fait de <xref:System.Span%601> le type préféré de fonctionnement sur un bloc de mémoire, elle soumet également <xref:System.Span%601> à certaines restrictions majeures. Il est important de savoir quand utiliser un <xref:System.Span%601> et quand utiliser <xref:System.Memory%601>.

Voici nos recommandations quant à l’utilisation réussie de <xref:System.Memory%601> et de ses types associés. Notez que les conseils concernant <xref:System.Memory%601> et <xref:System.Span%601> s’appliquent également à <xref:System.ReadOnlyMemory%601> et à <xref:System.ReadOnlySpan%601>, sauf si c’est explicitement exclu.

**#1 de règle : pour une API synchrone, utilisez\<Span t> au lieu\<de Memory t> en tant que paramètre, si possible.**

<xref:System.Span%601> est plus polyvalente que <xref:System.Memory%601> et peut représenter une plus grande variété de mémoires tampons contiguës. <xref:System.Span%601> offre également de meilleures performances que <xref:System.Memory%601>. Enfin, vous pouvez utiliser la propriété <xref:System.Memory%601.Span?displayProperty=nameWithType> pour convertir une instance <xref:System.Memory%601> en <xref:System.Span%601>, bien que la conversion Span\<T >- to-Memory\<T > ne soit pas possible. Par conséquent, si vos appelants ont une instance <xref:System.Memory%601>, ils pourront de toute façon appeler vos méthodes avec des paramètres <xref:System.Span%601>.

L’utilisation d’un paramètre de type <xref:System.Span%601> au lieu d’un paramètre de type <xref:System.Memory%601> vous aide également à écrire une implémentation correcte de la méthode de consommation. Des vérifications automatiques au moment de la compilation vous permettent de garantir que vous ne tentez pas d’accéder à la mémoire tampon au-delà de votre bail de méthode (nous y reviendrons plus tard).

Vous devrez parfois utiliser un paramètre <xref:System.Memory%601> au lieu d’un paramètre <xref:System.Span%601>, même si vous êtes entièrement synchrone. Il est possible qu’une API dont vous dépendez n’accepte que des arguments <xref:System.Memory%601>. C’est bien, mais tenez compte des compromis impliqués par l’utilisation synchrone de <xref:System.Memory%601>.

<a name="rule-2" />

**#2 de règle : utilisez\<ReadOnlySpan t> ou\<ReadOnlyMemory t> si la mémoire tampon doit être en lecture seule.**

Dans les exemples précédents, la méthode `DisplayBufferToConsole` lit uniquement à partir de la mémoire tampon ; elle ne modifie pas le contenu de la mémoire tampon. La signature de méthode doit être modifiée comme suit.

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

En fait, si nous combinons cette règle et la règle 1, nous pouvons faire encore mieux et réécrire la signature de méthode comme suit :

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

La méthode `DisplayBufferToConsole` fonctionne désormais avec pratiquement chaque type de mémoire tampon imaginable : `T[]`, stockage alloué avec [stackalloc](../../csharp/language-reference/operators/stackalloc.md), et ainsi de suite. Vous pouvez même y passer directement une chaîne <xref:System.String> !

**#3 de règle : Si votre méthode accepte\<la mémoire t> `void`et retourne, vous ne devez pas\<utiliser l’instance Memory t> après le retour de la méthode.**

Ceci est lié au concept de « bail » mentionné précédemment. Un bail de méthode avec renvoi d’annulation sur l’instance <xref:System.Memory%601> commence lorsqu’on entre dans la méthode et se termine lorsqu’on la quitte. Prenons l’exemple suivant, qui appelle `Log` dans une boucle basée sur l’entrée à partir de la console.

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

Si `Log` est une méthode parfaitement synchrone, ce code se comporte comme prévu, car il n’y a qu’un seul consommateur actif de l’instance de la mémoire à un moment donné.
Mais imaginez plutôt que `Log` a cette implémentation.

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

Dans cette implémentation, `Log` enfreint son bail, car il tente toujours d’utiliser l’instance <xref:System.Memory%601> en arrière-plan après le retour de la méthode d’origine. La méthode `Main` pourrait muter la mémoire tampon pendant que `Log` tente de la lire, ce qui pourrait entraîner une altération des données.

Il y a de nombreuses manières de résoudre ce problème :

- La méthode `Log` peut retourner une <xref:System.Threading.Tasks.Task> au lieu de `void`, comme le fait l’implémentation suivante de la méthode `Log`.

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- À la place, `Log` peut plutôt être implémenté comme suit :

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**#4 de règle : Si votre méthode accepte une\<> de mémoire t et retourne une tâche, vous ne devez pas\<utiliser l’instance de mémoire t> une fois que la tâche est passée à un état terminal.**

Il s’agit simplement la variante asynchrone de la règle 3. La méthode `Log` de l’exemple précédent peut être écrite comme suit pour se conformer à cette règle :

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

Ici, « état terminal » signifie que la tâche passe à un état terminé, ayant généré une erreur ou annulé. En d’autres termes, « état terminal » signifie « tout ce qui provoquerait une attente lors du lancement ou de la poursuite de l’exécution. »

Ces conseils s’appliquent aux méthodes qui retournent <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, ou n’importe quel type similaire.

**#5 de règle : Si votre constructeur accepte\<la mémoire T> en tant que paramètre, les méthodes d’instance sur l’objet construit sont supposées\<être des consommateurs de l’instance de la mémoire t>.**

Prenons l’exemple suivant :

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

Ici, le constructeur`OddValueExtractor` accepte `ReadOnlyMemory<int>` comme paramètre de constructeur, si bien que le constructeur lui-même est un consommateur de l’instance `ReadOnlyMemory<int>` et que toutes les méthodes d’instance sur la valeur retournée sont également des consommateurs de l’instance `ReadOnlyMemory<int>` d’origine. Cela signifie que `TryReadNextOddValue` consomme l’instance `ReadOnlyMemory<int>`, même si l’instance n’est pas passée directement à la méthode `TryReadNextOddValue`.

**#6 de règle : Si vous disposez d’une\<propriété de type mémoire t> définissable (ou d’une méthode d’instance équivalente) sur votre type, les méthodes d’instance sur cet objet sont\<supposées être des consommateurs de l’instance de la mémoire T>.**

Il s’agit simplement d’une variante de la règle 5. Cette règle existe, car les setters de propriété ou les méthodes équivalentes sont supposés capturer et conserver leurs entrées, de manière que les méthodes d’instances sur le même objet puissent utiliser l’état de capture.

L'exemple suivant déclenche cette règle :

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

**#7 de règle : Si vous avez une\<référence IMemoryOwner T>, vous devez à un moment l’éliminer ou transférer sa propriété (mais pas les deux).**

Dans la mesure où une instance <xref:System.Memory%601> peut être sauvegardée par de la mémoire, managée ou non, le propriétaire doit appeler <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> lorsque le travail effectué sur l’instance <xref:System.Memory%601> est terminé. Le propriétaire peut également transférer la propriété de l’instance <xref:System.Buffers.IMemoryOwner%601> à un autre composant. Le composant d’acquisition devient alors responsable de l’appel de <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> au moment opportun (nous y reviendrons plus tard).

Ne pas appeler la méthode <xref:System.Buffers.MemoryPool%601.Dispose%2A> peut entraîner des fuites de mémoire non managée ou une autre dégradation des performances.

Cette règle s’applique également au code qui appelle les méthodes de fabrique, telles que <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>. L’appelant devient le propriétaire du <xref:System.Buffers.IMemoryOwner%601> retourné et est responsable de la suppression de l’instance terminée.

**#8 de règle : Si vous avez un\<paramètre IMemoryOwner T> dans la surface de l’API, vous acceptez la propriété de cette instance.**

Accepter une instance de ce type signale que votre composant a l’intention de prendre possession de cette instance. Votre composant devient responsable de la suppression correcte conformément à la règle 7.

Tout composant qui transfère la propriété de l’instance <xref:System.Buffers.IMemoryOwner%601> à un autre composant ne doit plus utiliser cette instance lorsque l’appel de méthode se termine.

> [!IMPORTANT]
> Si votre constructeur accepte <xref:System.Buffers.IMemoryOwner%601> comme paramètre, son type doit implémenter <xref:System.IDisposable> et votre méthode <xref:System.IDisposable.Dispose%2A> doit appeler <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.

**#9 de règle : Si vous encapsulez une méthode p/Invoke synchrone, votre API doit\<accepter l’étendue T> en tant que paramètre.**

Conformément à la règle 1, <xref:System.Span%601> est généralement le type correct à utiliser pour les API synchrones. Vous pouvez épingler des instances <xref:System.Span%601> via le mot clé [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) mot clé, comme dans l’exemple suivant.

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

Dans l’exemple précédent, `pbData` peut être Null si, par exemple, l’étendue d’entrée est vide. Si la méthode exportée requiert absolument que `pbData` soit non Null, même si `cbData` est égal à 0, la méthode peut être implémentée comme suit :

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

**#10 de règle : Si vous encapsulez une méthode p/Invoke asynchrone, votre API doit\<accepter la mémoire T> en tant que paramètre.**

Étant donné que vous ne [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) pouvez pas utiliser le mot clé dans les <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> opérations asynchrones <xref:System.Memory%601> , vous utilisez la méthode pour épingler des instances, quel que soit le type de mémoire contiguë représenté par l’instance. L’exemple suivant montre comment utiliser cette API pour effectuer un appel p/invoke asynchrone.

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

## <a name="see-also"></a>Voir aussi

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
