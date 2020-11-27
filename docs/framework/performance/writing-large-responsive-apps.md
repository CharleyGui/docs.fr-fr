---
title: Conception d'applications .NET Framework complexes et réactives
description: Écrivez des applications .NET volumineuses et réactives ou des applications qui traitent une grande quantité de données, telles que des fichiers ou des bases de données.
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 20b9f34595f8586eb5162715eb6b0df171f132a1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266842"
---
# <a name="writing-large-responsive-net-framework-apps"></a>Conception d'applications .NET Framework complexes et réactives

Cet article fournit des conseils pour améliorer les performances d'applications .NET Framework volumineuses ou d'applications qui traitent de grandes quantités de données, telles que des fichiers ou des bases de données. Ces conseils proviennent de la réécriture des compilateurs C# et Visual Basic en code managé, et cet article inclut plusieurs exemples réels issus du compilateur C#.
  
Le .NET Framework est hautement productif pour la création d'applications. Des langages puissants et sécurisés, ainsi qu’une riche collection de bibliothèques, favorisent une création d’applications très fructueuse. Toutefois, une grande productivité implique des responsabilités. Vous devez utiliser toute la puissance du .NET Framework, mais vous devez être prêt à régler les performances de votre code lorsque cela est nécessaire.
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a>Raisons pour lesquelles les performances des nouveaux compilateurs s'appliquent à votre application  

 L'équipe chargée de la plateforme des compilateurs .NET (« Roslyn ») a réécrit les compilateurs C# et Visual Basic en code managé pour fournir de nouvelles API afin de modéliser et analyser le code, de créer des outils et de favoriser des expériences de programmation nettement plus riches dans Visual Studio. La réécriture des compilateurs et la création d'expériences Visual Studio sur les nouveaux compilateurs ont été source de riches enseignements en matière de performances, qui sont transposables à toute application .NET Framework volumineuse et à toute application qui traite une grande quantité de données. Vous n'avez pas besoin de connaître les compilateurs pour tirer profit des enseignements et des exemples issus du compilateur C#.
  
 Visual Studio utilise les API de compilateur pour générer toutes les fonctionnalités IntelliSense tant appréciées des utilisateurs, telles que la colorisation des identificateurs et des mots clés, les listes de saisie semi-automatique de syntaxe, les tildes d’erreur, les paramètres conseillés, les problèmes de code et les actions de code. Visual Studio fournit cette aide pendant que les développeurs saisissent et modifient leur code, et Visual Studio doit rester réactif pendant que le compilateur modélise de façon continue le code que les développeurs modifient.
  
 Quand vos utilisateurs finaux interagissent avec votre application, ils attendent d'elle qu'elle soit réactive. La saisie ou la gestion des commandes ne doivent jamais être bloquées. De l'aide doit s'afficher rapidement ou disparaître si l'utilisateur poursuit la saisie. Votre application doit éviter de bloquer le thread d'interface utilisateur avec de longs calculs qui donnent l'impression que l'application ne réagit pas.
  
 Pour plus d’informations sur les compilateurs Roslyn, consultez [le kit de développement logiciel (SDK) .NET Compiler Platform](../../csharp/roslyn-sdk/index.md).
  
## <a name="just-the-facts"></a>Les faits  

 Prenez en compte les faits suivants lorsque vous réglez les performances de vos applications .NET Framework pour les rendre plus réactives.
  
### <a name="fact-1-dont-prematurely-optimize"></a>Fait n° 1 : N'optimisez pas prématurément  

 L'écriture d'un code plus complexe que nécessaire entraîne des coûts de maintenance, de débogage et de finition. Les programmeurs expérimentés ont une compréhension intuitive de la manière de résoudre les problèmes de codage et écrivent des codes plus efficaces. Toutefois, ils optimisent parfois prématurément leur code. Par exemple, ils utilisent une table de hachage lorsqu'un simple tableau suffirait, ou ils utilisent une mise en cache compliquée susceptible d'engendrer des fuites de mémoire au lieu de simplement recalculer les valeurs. Même si vous êtes un programmeur expérimenté, vous devez tester les performances et analyser votre code quand vous décelez des problèmes.
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a>Fait n° 2 : Si vous n'effectuez pas de mesures, vous ne faites que supposer  

 Les profils et les mesures ne trompent pas. Les profils vous montrent si l'UC est pleinement chargée ou si vous êtes bloqué au niveau des E/S de disque. Les profils indiquent le type et la quantité de mémoire que vous allouez et si le processus [garbage collection](../../standard/garbage-collection/index.md) (GC) utilise beaucoup de ressources de votre UC.
  
 Vous devez définir des objectifs de performances pour des scénarios ou des expériences clients clés dans votre application, et écrire des tests pour mesurer les performances. Étudiez les échecs des tests en appliquant un raisonnement scientifique : utilisez des profils pour vous guider, avancez des hypothèses concernant la nature du problème et testez vos hypothèses en faisant des expériences ou en apportant des modifications au code. Établissez des mesures de performances de planning de référence au fil du temps en effectuant des tests réguliers, afin de pouvoir isoler les changements qui provoquent des régressions des performances. Grâce à une approche rigoureuse du traitement des performances, vous éviterez de perdre du temps avec des mises à jour de code inutiles.
  
### <a name="fact-3-good-tools-make-all-the-difference"></a>Fait n° 3 : Des outils efficaces font toute la différence  

 Des outils efficaces vous permettent de plonger directement au cœur des principaux problèmes de performances (UC, mémoire ou disque) et vous aident à localiser le code à l'origine des goulots d'étranglement. Microsoft fournit un large éventail d’outils de performances, tels que le [profileur Visual Studio](/visualstudio/profiling/beginners-guide-to-performance-profiling) et [PerfView](https://www.microsoft.com/download/details.aspx?id=28567).
  
 PerfView est un outil gratuit et extrêmement puissant qui vous permet de porter toute votre attention sur des problèmes profonds liés par exemple aux E/S de disque, aux événements du GC et à la mémoire. Vous pouvez capturer des événements de [suivi d’événements pour Windows](../wcf/samples/etw-tracing.md) (ETW) liés aux performances et afficher aisément les informations pour chaque application, processus, pile et thread. PerfView vous montre la quantité et le type de mémoire que votre application alloue, ainsi que les fonctions ou les piles d'appels qui contribuent aux allocations de mémoire, et pour quels volumes. Pour plus de détails, consultez l’ensemble complet de rubriques d’aide, de démonstrations et de vidéos fournies avec l’outil (par exemple, les [didacticiels PerfView](https://channel9.msdn.com/Series/PerfView-Tutorial) sur Channel 9).
  
### <a name="fact-4-its-all-about-allocations"></a>Fait n° 4 : Tout se résume aux allocations  

 Vous pouvez penser que la création d'une application .NET Framework réactive n'est qu'une question d'algorithmes, comme l'utilisation d'un tri rapide à la place d'un tri par propagation, mais ce n'est pas le cas. Le facteur principal qui intervient dans la création d'une application réactive et l'allocation de la mémoire, notamment quand votre application est très volumineuse ou traite de grandes quantités de données.
  
 Quasiment tout le travail nécessaire pour créer des expériences IDE réactives avec les API des nouveaux compilateurs a impliqué d’éviter les allocations et de gérer les stratégies de mise en cache. Les traces PerfView indiquent que les performances des nouveaux compilateurs C# et Visual Basic sont rarement liées à l'UC. Les compilateurs peuvent être liés aux E/S lors de la lecture de centaines de milliers ou de millions de lignes de code, lors de la lecture des métadonnées ou lors de l'émission du code généré. Les retards de threads d’interface utilisateur sont quasiment tous dus au garbage collection. Le GC du .NET Framework fait l'objet d'un réglage précis pour les performances et effectue une grande part de son travail pendant que le code de l'application s'exécute. Toutefois, une seule allocation peut déclencher une collection [gen2](../../standard/garbage-collection/fundamentals.md) coûteuse, susceptible d’arrêter tous les threads.
  
## <a name="common-allocations-and-examples"></a>Allocations courantes et exemples courants  

 Les exemples d'expressions fournis dans cette section possèdent des allocations masquées qui apparaissent réduites. Toutefois, si une application volumineuse exécute ces expressions suffisamment de fois, elles peuvent entraîner l'allocation de centaines de méga-octets, voire même de plusieurs giga-octets, de mémoire. Par exemple, des tests d'une minute simulant une phase de saisie par un développeur dans l'éditeur ont alloué plusieurs giga-octets de mémoire et conduit l'équipe de performances à se concentrer sur des scénarios de saisie.
  
### <a name="boxing"></a>Boxing  

 Le [boxing](../../csharp/programming-guide/types/boxing-and-unboxing.md) intervient quand des types valeur situés normalement sur la pile ou dans des structures de données sont encapsulés dans un objet. Autrement dit, vous allouez un objet pour contenir les données, puis retournez un pointeur vers cet objet. Le .NET Framework effectue parfois le boxing de certaines valeurs en raison de la signature d'une méthode ou du type d'un emplacement de stockage. L'encapsulation d'un type valeur dans un objet entraîne une allocation de mémoire. De nombreuses opérations de boxing peuvent favoriser l'allocation de méga-octets ou de giga-octets de mémoire dans votre application, ce qui signifie que cette dernière entraînera encore plus d'opérations de GC. Le .NET Framework et les compilateurs de langage évitent le boxing autant que possible, mais parfois il intervient quand vous vous y attendez le moins.
  
 Pour voir le boxing dans PerfView, ouvrez une trace et examinez les piles d'allocation de tas GC sous le nom du processus de votre application (souvenez-vous, PerfView fournit des rapports sur tous les processus). Si vous voyez des types tels que <xref:System.Int32?displayProperty=nameWithType> et <xref:System.Char?displayProperty=nameWithType> sous les allocations, vous effectuez le boxing de types valeur. La sélection d'un de ces types vous montrera les piles et les fonctions dans lesquelles le boxing s'effectue.
  
 **Exemple 1 : méthodes string et arguments de type valeur**  
  
 Cet exemple de code illustre un boxing potentiellement inutile et excessif :  
  
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
  
 Ce code fournit des fonctionnalités de journalisation qui permettent à une application d'appeler la fonction `Log` fréquemment, éventuellement des millions de fois. Le problème est que l'appel de `string.Format` se traduit par la surcharge <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29>.
  
 Cette surcharge oblige le .NET Framework à effectuer le boxing des valeurs `int` en objets pour les passer à cet appel de méthode. Une correction partielle consiste à appeler `id.ToString()` et `size.ToString()`, et à passer toutes les chaînes (qui sont des objets) à l'appel de `string.Format`. L'appel de `ToString()` n'alloue pas de chaîne, mais cette allocation aura lieu quoi qu'il en soit dans `string.Format`.
  
 Vous pouvez considérer que cet appel élémentaire à `string.Format` est une simple concaténation de chaînes, et vous pouvez écrire le code suivant à la place :  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 Toutefois, cette ligne de code introduit une allocation de boxing car elle est compilée en <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>. Le .NET Framework doit effectuer le boxing du littéral de caractère pour appeler `Concat`.  
  
 **Correctif pour l’exemple 1**  
  
 Le correctif complet est simple. Remplacez simplement le littéral de caractère par un littéral de chaîne. Cela n'entraîne pas de boxing car les chaînes sont déjà des objets :  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 **Exemple 2 : boxing d’enums**  
  
 Cet exemple était responsable de l'allocation d'une énorme quantité de mémoire dans les nouveaux compilateurs C# et Visual Basic en raison de l'utilisation fréquente des types énumération, notamment dans les opérations de consultation de dictionnaire.
  
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
  
 Ce problème est très subtil. PerfView rapporterait cela en tant que boxing <xref:System.Enum.GetHashCode>, car la méthode effectue le boxing de la représentation sous-jacente du type énumération, pour des raisons d'implémentation. Si vous examinez attentivement PerfView, vous pouvez voir deux allocations de boxing pour chaque appel à <xref:System.Enum.GetHashCode>. Le compilateur en insère une et le .NET Framework insère l'autre.
  
 **Correctif pour l’exemple 2**  
  
 Vous pouvez aisément éviter ces deux allocations en effectuant un cast vers la représentation sous-jacente avant d'appeler <xref:System.Enum.GetHashCode> :  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 Une autre source courante de boxing sur des types énumération est la méthode <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType>. L’argument passé à <xref:System.Enum.HasFlag%28System.Enum%29> doit faire l’objet du boxing. Dans la plupart des cas, le remplacement des appels à <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> par un test au niveau du bit est plus simple et n'entraîne pas d'allocation.
  
 Gardez à l'esprit le premier fait énoncé sur les performances (ne pas optimiser prématurément) et ne commencez pas à réécrire tout votre code de cette manière. Soyez conscient des coûts du boxing, mais modifiez votre code une fois seulement que vous aurez profilé votre application et trouvé les points sensibles.
  
### <a name="strings"></a>Chaînes  

 Les manipulations de chaînes comptent parmi les plus grands responsables d'allocations, et figurent souvent dans PerfView dans les cinq premières allocations. Les programmes utilisent des chaînes pour les interfaces API de sérialisation, JSON et REST. Vous pouvez utiliser des chaînes en tant que constantes de programmation pour interagir avec des systèmes quand vous ne pouvez pas utiliser les types énumération. Quand votre profilage montre que les chaînes affectent grandement les performances, recherchez les appels aux méthodes <xref:System.String> tels que <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, etc. Il est utile d'avoir recours à <xref:System.Text.StringBuilder> pour éviter le coût de la création d'une seule chaîne à partir de nombreux composants, mais même l'allocation de l'objet <xref:System.Text.StringBuilder> peut devenir un goulot d'étranglement que vous devrez gérer.
  
 **Exemple 3 : opérations de chaînes**  
  
 Le compilateur C# possédait ce code qui écrit le texte d'un commentaire de document XML formaté :  
  
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
  
 Vous pouvez constater que ce code effectue beaucoup de manipulations de chaînes. Le code utilise des méthodes de bibliothèque pour séparer les lignes en chaînes distinctes, pour découper l’espace blanc, pour vérifier si l’argument `text` est un commentaire de documentation XML et pour extraire des sous-chaînes des lignes.
  
 À la première ligne dans `WriteFormattedDocComment`, l’appel `text.Split` alloue un nouveau tableau à trois éléments comme argument chaque fois qu’il est appelé. Le compilateur doit émettre du code pour allouer ce tableau chaque fois. En effet, le compilateur ne sait pas si <xref:System.String.Split%2A> stocke le tableau quelque part où il pourrait être modifié par un autre code, ce qui affecterait ultérieurement les appels à `WriteFormattedDocComment`. L'appel à <xref:System.String.Split%2A> alloue également une chaîne pour chaque ligne dans `text` et alloue encore de la mémoire pour effectuer l'opération.
  
 `WriteFormattedDocComment` possède trois appels à la méthode <xref:System.String.TrimStart%2A>. Deux se trouvent dans des boucles internes qui dupliquent le travail et les allocations. Pour aggraver encore la situation, appeler la méthode <xref:System.String.TrimStart%2A> sans argument alloue un tableau vide (pour le paramètre `params`) en plus de la chaîne résultante.
  
 Enfin, il existe un appel à la méthode <xref:System.String.Substring%2A>, qui alloue habituellement une nouvelle chaîne.
  
 **Correctif pour l’exemple 3**  
  
 À la différence des exemples précédents, de petites modifications ne peuvent pas corriger ces allocations. Vous devez prendre du recul, examiner le problème et tenter une approche différente. Par exemple, vous pouvez noter que l'argument pour `WriteFormattedDocComment()` est une chaîne qui possède toutes les informations dont la méthode a besoin, de sorte que le code pourrait effectuer une indexation supplémentaire au lieu d'allouer de nombreuses chaînes partielles.
  
 L’équipe de performances du compilateur s’est attaquée à toutes ces allocations avec du code similaire à :  
  
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
  
 La première version de `WriteFormattedDocComment()` allouait un tableau, plusieurs sous-chaînes et une sous-chaîne tronquée avec un tableau `params` vide. Il a également été vérifié pour « /// ». Le code révisé utilise uniquement l'indexation et n'alloue rien. Il recherche le premier caractère qui n’est pas un espace blanc, puis vérifie caractère par caractère pour voir si la chaîne commence par « /// ». Le nouveau code utilise `IndexOfFirstNonWhiteSpaceChar` à la place de <xref:System.String.TrimStart%2A> pour retourner le premier index (après un index de début spécifié) où un caractère autre qu’un espace blanc se produit. Le correctif n'est pas complet, mais vous pouvez voir comment appliquer des correctifs similaires pour obtenir une solution complète. En appliquant cette approche dans l'ensemble du code, vous pouvez supprimer toutes les allocations dans `WriteFormattedDocComment()`.
  
 **Exemple 4 : StringBuilder**  
  
 Cet exemple utilise un objet <xref:System.Text.StringBuilder>. La fonction suivante génère un nom de type complet pour des types génériques :  
  
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
  
 Le focus est sur la ligne qui crée une nouvelle instance <xref:System.Text.StringBuilder>. Le code génère une allocation pour `sb.ToString()` et des allocations internes au sein de l'implémentation <xref:System.Text.StringBuilder>, mais vous ne pouvez pas contrôler ces allocations si vous souhaitez la chaîne résultante.
  
 **Correctif pour l’exemple 4**  
  
 Pour corriger l'allocation de l'objet `StringBuilder`, mettez en cache l'objet. Même la mise en cache d'une instance unique susceptible d'être jetée peut améliorer les performances de manière significative. Il s'agit de la nouvelle implémentation de la fonction, qui omet tout le code à l'exception des nouvelles première et dernière lignes :  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 Les composants clés sont les nouvelles fonctions `AcquireBuilder()` et `GetStringAndReleaseBuilder()` :  
  
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
  
 Comme les nouveaux compilateurs utilisent le threading, ces implémentations utilisent un champ static de thread (attribut <xref:System.ThreadStaticAttribute>) pour mettre en cache <xref:System.Text.StringBuilder>, et vous pouvez probablement vous passer de la déclaration `ThreadStatic`. Le champ static de thread contient une valeur unique pour chaque thread qui exécute ce code.
  
 `AcquireBuilder()` retourne l'instance <xref:System.Text.StringBuilder> mise en cache, le cas échéant, après l'avoir effacée et avoir défini le champ ou le cache sur Null. Dans le cas contraire, `AcquireBuilder()` crée une nouvelle instance et la retourne, laissant le champ ou le cache défini sur Null.
  
 Une fois que vous avez terminé avec <xref:System.Text.StringBuilder>, vous appelez `GetStringAndReleaseBuilder()` pour obtenir la chaîne résultante, enregistrez l'instance <xref:System.Text.StringBuilder> dans le champ ou le cache, puis retournez le résultat. Il est possible pour l'exécution d'entrer une nouvelle fois ce code et de créer plusieurs objets <xref:System.Text.StringBuilder> (bien que cela se produise rarement). Le code enregistre uniquement la dernière instance <xref:System.Text.StringBuilder> libérée pour une utilisation ultérieure. Cette stratégie de mise en cache simple a réduit considérablement les allocations dans les nouveaux compilateurs. Certains composants de .NET Framework et de MSBuild (« MSBuild ») utilisent une technique similaire pour améliorer les performances.
  
 Cette stratégie de mise en cache simple est conforme à une conception de cache satisfaisante car elle possède une taille seuil. Toutefois, il y a plus de code maintenant que dans l'original, ce qui induit des coûts de maintenance supérieurs. Vous devez adopter la stratégie de mise en cache seulement si vous avez trouvé un problème de performances et que PerfView a montré que les allocations <xref:System.Text.StringBuilder> constituent un contributeur important.
  
### <a name="linq-and-lambdas"></a>Expressions LINQ et lambda  

Language-Integrated query (LINQ), conjointement avec les expressions lambda, est un exemple de fonctionnalité de productivité. Toutefois, son utilisation peut avoir un impact significatif sur les performances au fil du temps, et vous pouvez être amené à réécrire votre code.
  
 **Exemple 5 : expressions lambda, liste \<T> et IEnumerable\<T>**  
  
 Cet exemple utilise du [code de style opérationnel et LINQ](/archive/blogs/charlie/anders-hejlsberg-on-linq-and-functional-programming) pour rechercher un symbole dans le modèle du compilateur, selon une chaîne de nom :  
  
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
  
 Le nouveau compilateur et les expériences IDE construites dessus appellent `FindMatchingSymbol()` très fréquemment, et il existe plusieurs allocations masquées dans la seule ligne de code de cette fonction. Pour examiner ces allocations, commencer par séparer la seule ligne de code de la fonction en deux lignes :  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 Dans la première ligne, l’[expression lambda](../../csharp/language-reference/operators/lambda-expressions.md) `s => s.Name == name` [ se ferme par-dessus](/archive/blogs/ericlippert/what-are-closures) la variable locale `name`. Cela signifie qu’en plus d’allouer un objet pour le [délégué](../../csharp/language-reference/builtin-types/reference-types.md#the-delegate-type) contenu dans `predicate`, le code alloue une classe statique pour contenir l’environnement qui capture la valeur de `name`. Le compilateur génère un code similaire au suivant :  
  
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
  
 Les deux allocations `new` (une pour la classe d'environnement et l'autre pour le délégué) sont désormais explicites.
  
 À présent, examinez l'appel à `FirstOrDefault`. Cette méthode d'extension sur le type <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> induit également une allocation. Comme `FirstOrDefault` accepte un objet <xref:System.Collections.Generic.IEnumerable%601> comme premier argument, vous pouvez développer l'appel au code suivant (légèrement simplifié pour cette présentation) :  
  
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
  
 La variable `symbols` possède le type <xref:System.Collections.Generic.List%601>. Le type de collection <xref:System.Collections.Generic.List%601> implémente <xref:System.Collections.Generic.IEnumerable%601> et définit intelligemment un énumérateur (interface <xref:System.Collections.Generic.IEnumerator%601>) que <xref:System.Collections.Generic.List%601> implémente avec un `struct`. L'utilisation d'une structure à la place d'une classe signifie que vous évitez habituellement toutes les allocations de tas, lesquelles, à leur tour, peuvent affecter les performances de garbage collection. Les énumérateurs sont généralement utilisés avec la boucle `foreach` du langage, qui utilise la structure des énumérateurs lorsqu'elle est renvoyée sur la pile d'appels. L'incrémentation du pointeur de la pile d'appels pour faire de la place pour un objet n'affecte pas le GC comme le fait une allocation de tas.
  
 Dans le cas de l'appel `FirstOrDefault` développé, le code a besoin d'appeler `GetEnumerator()` sur un <xref:System.Collections.Generic.IEnumerable%601>. L'affectation de `symbols` à la variable `enumerable` du type `IEnumerable<Symbol>` entraîne la perte des informations indiquant que l'objet réel est un <xref:System.Collections.Generic.List%601>. Cela signifie que quand le code récupère l’énumérateur avec `enumerable.GetEnumerator()`, le .NET Framework doit effectuer le boxing de la structure renvoyée pour l’affecter à la variable `enumerator`.
  
 **Correctif pour l’exemple 5**  
  
 Le correctif consiste à réécrire `FindMatchingSymbol` comme suit, en remplaçant sa ligne de code unique par six lignes de code qui restent concises, faciles à lire et à comprendre, et aisées à tenir à jour :  
  
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
  
 Ce code n'utilise pas d'énumérateurs, d'expressions lambda ni de méthodes d'extension LINQ, et il n'induit pas d'allocations. L’absence d’allocation vient du fait que le compilateur peut voir que la collection `symbols` est une classe <xref:System.Collections.Generic.List%601> et qu’elle peut lier l’énumérateur résultant (une structure) à une variable locale avec le type correct pour éviter le boxing. La version originale de cette fonction était un exemple parfait de la puissance expressive de C# et de la productivité du .NET Framework. Cette nouvelle version, plus efficace, conserve ces qualités sans ajouter de code complexe à tenir à jour.
  
### <a name="async-method-caching"></a>Mise en cache dans les méthodes async  

L’exemple suivant illustre un problème courant qui se produit quand vous essayez d’utiliser des résultats en cache dans une méthode [async](../../csharp/programming-guide/concepts/async/index.md).
  
 **Exemple 6 : mise en cache dans les méthodes async**  
  
 Les fonctionnalités IDE de Visual Studio qui s'appuient sur les nouveaux compilateurs C# et Visual Basic récupèrent fréquemment des arborescences de syntaxe, et les compilateurs utilisent async à cette occasion pour maintenir la réactivité de Visual Studio. Voici la première version du code que vous pouvez écrire afin d'obtenir une arborescence de syntaxe :  
  
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
  
 Vous pouvez voir que l'appel à `GetSyntaxTreeAsync()` instancie un `Parser`, analyse le code, puis retourne un objet <xref:System.Threading.Tasks.Task>, `Task<SyntaxTree>`. La partie coûteuse correspond à l'allocation de l'instance `Parser` et à l'analyse du code. La fonction retourne une classe <xref:System.Threading.Tasks.Task> afin que les appelants puissent attendre le travail d'analyse et libérer le thread d'interface utilisateur pour être réactifs à l'entrée d'utilisateur.
  
 Plusieurs fonctionnalités Visual Studio peuvent essayer d’obtenir la même arborescence de syntaxe. Vous pouvez donc écrire le code suivant pour mettre en cache le résultat d’analyse pour économiser du temps et des allocations. Toutefois, ce code induit une allocation :  
  
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
  
 Vous constatez que le nouveau code avec la mise en cache possède un champ `SyntaxTree` nommé `cachedResult`. Quand ce champ à la valeur null, `GetSyntaxTreeAsync()` effectue le travail et enregistre le résultat dans le cache. `GetSyntaxTreeAsync()` retourne l'objet `SyntaxTree`. Le problème tient au fait que lorsque vous avez une fonction `async` de type `Task<SyntaxTree>` et que vous retournez une valeur de type `SyntaxTree`, le compilateur émet du code pour allouer un objet Task pour contenir le résultat (en utilisant `Task<SyntaxTree>.FromResult()`). L’objet Task est marqué comme terminé et le résultat est disponible immédiatement. Dans le code pour les nouveaux compilateurs, des objets <xref:System.Threading.Tasks.Task> déjà terminés se manifestaient si souvent que la correction de ces allocations a amélioré notablement la réactivité.
  
 **Correctif pour l’exemple 6**  
  
 Pour supprimer l' <xref:System.Threading.Tasks.Task> allocation terminée, vous pouvez mettre en cache l’objet Task avec le résultat terminé :  
  
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
  
 Ce code change le type de `cachedResult` en `Task<SyntaxTree>` et emploie une fonction d'assistance `async` qui contient le code original issu de `GetSyntaxTreeAsync()`. `GetSyntaxTreeAsync()` utilise maintenant l’[opérateur de fusion Null](../../csharp/language-reference/operators/null-coalescing-operator.md) pour retourner `cachedResult` s’il n’a pas la valeur Null. Si `cachedResult` a la valeur Null, alors `GetSyntaxTreeAsync()` appelle `GetSyntaxTreeUncachedAsync()` et met en cache le résultat. Notez que `GetSyntaxTreeAsync()` n'attend pas l'appel à `GetSyntaxTreeUncachedAsync()` comme le ferait normalement le code. Ne pas utiliser d'attente signifie que quand `GetSyntaxTreeUncachedAsync()` retourne son objet <xref:System.Threading.Tasks.Task>, `GetSyntaxTreeAsync()` retourne immédiatement l'objet <xref:System.Threading.Tasks.Task>. À présent, le résultat mis en cache est un objet <xref:System.Threading.Tasks.Task>, d'où l'absence d'allocation pour retourner le résultat mis en cache.
  
### <a name="additional-considerations"></a>Considérations supplémentaires  

 Vous trouverez ci-dessous quelques points supplémentaires concernant des problèmes susceptibles de survenir dans des applications volumineuses ou qui traitent de grandes quantités de données.
  
 **Dictionnaires**  
  
 Les dictionnaires sont utilisés de façon omniprésente dans de nombreux programmes. Malgré cela, ils sont très pratiques et intrinsèquement efficaces. Toutefois, ils sont souvent utilisés de façon inappropriée. Dans Visual Studio et les nouveaux compilateurs, l'analyse montre qu'un grand nombre des dictionnaires contenaient un seul élément ou étaient vides. Un objet <xref:System.Collections.Generic.Dictionary%602> vide possède dix champs et occupe 48 octets sur le tas, sur un ordinateur x86. Les dictionnaires sont très utiles lorsque vous avez besoin d'un mappage ou d'une structure de données associative avec une recherche constante. Toutefois, quand vous ne possédez que quelques éléments, vous gaspillez beaucoup d'espace en utilisant un dictionnaire. À la place, par exemple, vous pourriez examiner de façon itérative un `List<KeyValuePair\<K,V>>`, tout aussi rapidement. Si vous utilisez un dictionnaire seulement pour le charger avec des données, puis lire à partir de cet objet (un modèle très courant), l’utilisation d’un tableau trié avec une recherche N(log(N)) peut être quasiment aussi rapide, selon le nombre d’éléments que vous utilisez.
  
 **Classes et structures**  
  
 D'une certaine façon, les classes et les structures fournissent un compromis standard entre espace et temps pour le réglage de vos applications. Les classes induisent une surcharge de 12 octets sur un ordinateur x86 même si elles ne possèdent pas de champ, mais elles n'induisent pas de coût pour être passées, car seul un pointeur est nécessaire pour faire référence à une instance de classe. Les structures n'induisent pas d'allocations de tas si elles ne font pas l'objet d'un boxing, mais quand vous passez de grandes structures en tant qu'arguments de fonction ou valeurs de retour, la copie atomique de toutes les données membres des structures consomme du temps processeur. Surveillez les appels répétés à des propriétés qui retournent des structures et mettez en cache la valeur de la propriété dans une variable locale pour éviter la copie excessive de données.
  
 **Caches**  
  
 Une astuce courante liée aux performances consiste à mettre en cache les résultats. Toutefois, un cache dépourvu d'une taille seuil ou d'une stratégie de suppression peut engendrer une fuite de mémoire. Quand vous traitez de grandes quantités de données, si vous conservez une grande quantité de mémoire dans des caches, le garbage collection risque de contrebalancer les avantages de vos recherches en cache.
  
 Dans cet article, nous avons vu que vous devez être conscient des symptômes de goulot d'étranglement de performances qui peuvent affecter la réactivité de votre application, notamment pour les grands systèmes et les systèmes qui traitent de grandes quantités de données. Les facteurs courants incluent le boxing, les manipulations de chaînes, les expressions LINQ et lambda, la mise en cache dans les méthodes async, la mise en cache sans taille limite ou stratégie de suppression, l'utilisation inappropriée des dictionnaires et le fait de passer des structures. Gardez à l'esprit les quatre faits liés au réglage de vos applications :  
  
- N'optimisez pas prématurément : soyez productif et réglez votre application quand vous détectez des problèmes.
  
- Les profils ne trompent pas : sans mesures, vous ne faites que supposer.
  
- Des outils efficaces font toute la différence : téléchargez PerfView et essayez-le.
  
- Tout se résume aux allocations : c'est dans ce domaine que l'équipe chargée de la plateforme des compilateurs a passé le plus de temps à améliorer les performances des nouveaux compilateurs.
  
## <a name="see-also"></a>Voir aussi

- [Vidéo de présentation de cette rubrique](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)
- [Guide du débutant en profilage des performances](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Performances](index.md)
- [Conseils relatifs aux performances .NET](/previous-versions/dotnet/articles/ms973839(v=msdn.10))
- [Didacticiels PerfView sur Canal 9](https://channel9.msdn.com/Series/PerfView-Tutorial)
- [Kit SDK .NET Compiler Platform](../../csharp/roslyn-sdk/index.md)
- [dotnet/Roslyn référentiel sur GitHub](https://github.com/dotnet/roslyn)
