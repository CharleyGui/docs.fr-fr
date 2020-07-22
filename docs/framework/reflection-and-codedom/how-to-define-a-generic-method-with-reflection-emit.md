---
title: 'Procédure : définir une méthode générique avec l’émission de réflexion'
description: Définissez une méthode générique avec l’émission de réflexion. Un exemple crée une méthode générique avec deux paramètres de type. Un deuxième exemple montre comment émettre le corps de la méthode.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic methods
- generics [.NET Framework], dynamic types
ms.assetid: 93892fa4-90b3-4ec4-b147-4bec9880de2b
ms.openlocfilehash: 3b85fb480e5862daa3b2800f75392adbe92348f2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865136"
---
# <a name="how-to-define-a-generic-method-with-reflection-emit"></a>Procédure : définir une méthode générique avec l’émission de réflexion

La première procédure montre comment créer une méthode générique simple avec deux paramètres de type et comment appliquer des contraintes de classe, des contraintes d’interface et des contraintes spéciales aux paramètres de type.

La deuxième procédure montre comment émettre le corps de la méthode et comment utiliser les paramètres de type de la méthode générique pour créer des instances des types génériques et appeler leurs méthodes.

La troisième procédure montre comment appeler la méthode générique.

> [!IMPORTANT]
> Une méthode n’est pas générique simplement car elle appartient à un type générique et utilise les paramètres de type de ce type. Une méthode est générique uniquement si elle a sa propre liste de paramètres de type. Une méthode générique peut apparaître sur un type non générique, comme dans cet exemple. Pour obtenir un exemple de méthode non générique sur un type générique, consultez [Guide pratique pour définir un type générique avec l’émission de réflexion](how-to-define-a-generic-type-with-reflection-emit.md).

### <a name="to-define-a-generic-method"></a>Pour définir une méthode générique

1. Avant de commencer, il est utile d’observer à quoi ressemble la méthode générique quand elle est écrite à l’aide d’un langage de haut niveau. Le code suivant est inclus dans l’exemple de code de cette rubrique, en plus du code pour appeler la méthode générique. La méthode a deux paramètres de type, `TInput` et `TOutput`, dont le second doit être un type référence (`class`), doit avoir un constructeur sans paramètre (`new`) et doit implémenter `ICollection(Of TInput)` (`ICollection<TInput>` en C#). Cette contrainte d’interface garantit que la méthode <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> peut être utilisée pour ajouter des éléments à la collection `TOutput` créée par la méthode. La méthode a un paramètre formel, `input`, qui est un tableau de `TInput`. La méthode crée une collection de type `TOutput` et copie les éléments de `input` dans la collection.

    [!code-csharp[GenericMethodHowTo#20](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#20)]
    [!code-vb[GenericMethodHowTo#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#20)]

2. Définissez un assembly dynamique et un module dynamique pour contenir le type auquel la méthode générique appartient. Dans ce cas, l’assembly n’a qu’un seul module, nommé `DemoMethodBuilder1`, et le nom du module est identique au nom de l’assembly plus une extension. Dans cet exemple, l’assembly est enregistré sur le disque et exécuté. <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> est donc spécifié. Vous pouvez utiliser le [désassembleur IL (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) pour examiner DemoMethodBuilder1.dll et la comparer au code MSIL (Microsoft Intermediate language) de la méthode illustrée à l’étape 1.

    [!code-csharp[GenericMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#2)]
    [!code-vb[GenericMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#2)]

3. Définissez le type auquel appartient la méthode générique. Il n’est pas obligatoire que le type soit générique. Une méthode générique peut appartenir à un type générique ou non générique. Dans cet exemple, le type est une classe, n’est pas générique et se nomme `DemoType`.

    [!code-csharp[GenericMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#3)]
    [!code-vb[GenericMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#3)]

4. Définissez la méthode générique. Si les types des paramètres formels d’une méthode générique sont spécifiés par les paramètres de type générique de la méthode générique, utilisez la surcharge de méthode <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%28System.String%2CSystem.Reflection.MethodAttributes%29> pour définir la méthode. Les paramètres de type générique de la méthode n’étant pas encore définis, vous ne pouvez pas spécifier les types des paramètres formels de la méthode dans l’appel à <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%2A>. Dans cet exemple, la méthode se nomme `Factory`. La méthode est publique et `static` (`Shared` en Visual Basic).

    [!code-csharp[GenericMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#4)]
    [!code-vb[GenericMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#4)]

5. Définissez les paramètres de type générique de `DemoMethod` en passant un tableau de chaînes contenant les noms des paramètres à la méthode <xref:System.Reflection.Emit.MethodBuilder.DefineGenericParameters%2A?displayProperty=nameWithType>. Cela rend la méthode générique. Le code suivant fait de `Factory` une méthode générique avec les paramètres de type `TInput` et `TOutput`. Pour faciliter la lecture du code, des variables avec ces noms sont créées pour stocker les objets <xref:System.Reflection.Emit.GenericTypeParameterBuilder> représentant les deux paramètres de type.

    [!code-csharp[GenericMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#5)]
    [!code-vb[GenericMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#5)]

6. Ajoutez éventuellement des contraintes spéciales aux paramètres de type. Les contraintes spéciales sont ajoutées à l’aide de la méthode <xref:System.Reflection.Emit.GenericTypeParameterBuilder.SetGenericParameterAttributes%2A>. Dans cet exemple, `TOutput` doit être un type référence et avoir un constructeur sans paramètre.

    [!code-csharp[GenericMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#6)]
    [!code-vb[GenericMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#6)]

7. Ajoutez éventuellement des contraintes de classe et d’interface aux paramètres de type. Dans cet exemple, le paramètre de type `TOutput` est limité aux types qui implémentent l’interface `ICollection(Of TInput)` (`ICollection<TInput>` en C#). Cela garantit que la méthode <xref:System.Collections.Generic.ICollection%601.Add%2A> peut être utilisée pour ajouter des éléments.

    [!code-csharp[GenericMethodHowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#7)]
    [!code-vb[GenericMethodHowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#7)]

8. Définissez les paramètres formels de la méthode, à l’aide de la méthode <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A>. Dans cet exemple, la méthode `Factory` a un paramètre, un tableau de `TInput`. Ce type est créé en appelant la méthode <xref:System.Type.MakeArrayType%2A> sur le <xref:System.Reflection.Emit.GenericTypeParameterBuilder> qui représente `TInput`. L’argument de <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> est un tableau d’objets <xref:System.Type>.

    [!code-csharp[GenericMethodHowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#8)]
    [!code-vb[GenericMethodHowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#8)]

9. Définissez le type de retour de la méthode, à l’aide de la méthode <xref:System.Reflection.Emit.MethodBuilder.SetReturnType%2A>. Dans cet exemple, une instance de `TOutput` est retournée.

    [!code-csharp[GenericMethodHowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#9)]
    [!code-vb[GenericMethodHowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#9)]

10. Émettez le corps de méthode à l’aide de <xref:System.Reflection.Emit.ILGenerator>. Pour plus d’informations, consultez la procédure d’émission du corps de méthode.

    > [!IMPORTANT]
    > Quand vous émettez des appels à des méthodes de types génériques et que les arguments de type de ces types sont des paramètres de type de la méthode générique, vous devez utiliser les surcharges de méthode `static`<xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29>, <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> et <xref:System.Reflection.Emit.TypeBuilder.GetField%28System.Type%2CSystem.Reflection.FieldInfo%29> de la classe <xref:System.Reflection.Emit.TypeBuilder> pour obtenir des formes construites des méthodes. Ceci est illustré dans la procédure d’émission du corps de méthode.

11. Terminez le type qui contient la méthode et enregistrez l’assembly. La procédure d’appel de la méthode générique montre deux façons d’appeler la méthode achevée.

    [!code-csharp[GenericMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#14)]
    [!code-vb[GenericMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#14)]

<a name="procedureSection1"></a>

### <a name="to-emit-the-method-body"></a>Pour émettre le corps de méthode

1. Obtenez un générateur de code et déclarez des étiquettes et des variables locales. La méthode <xref:System.Reflection.Emit.ILGenerator.DeclareLocal%2A> est utilisée pour déclarer des variables locales. La méthode `Factory` a quatre variables locales : `retVal` pour stocker le nouveau `TOutput` retourné par la méthode, `ic` pour contenir le `TOutput` quand il est converti en `ICollection(Of TInput)` (`ICollection<TInput>` en C#), `input` pour contenir le tableau d’entrée d’objets `TInput`, et `index` pour itérer le tableau. La méthode a également deux étiquettes, une pour entrer dans la boucle (`enterLoop`) et une pour le début de la boucle (`loopAgain`), définies à l’aide de la méthode <xref:System.Reflection.Emit.ILGenerator.DefineLabel%2A>.

    La première chose que fait la méthode est de charger son argument à l’aide de l’opcode <xref:System.Reflection.Emit.OpCodes.Ldarg_0> et de le stocker dans la variable locale `input` à l’aide de l’opcode <xref:System.Reflection.Emit.OpCodes.Stloc_S>.

    [!code-csharp[GenericMethodHowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#10)]
    [!code-vb[GenericMethodHowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#10)]

2. Émettez le code pour créer une instance de `TOutput`, à l’aide de la surcharge de méthode générique de la méthode <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>. L’utilisation de cette surcharge impose que le type spécifié ait un constructeur sans paramètre, ce qui explique pourquoi cette contrainte a été ajoutée à `TOutput`. Créez la méthode générique construite en passant `TOutput` à <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>. Après avoir émis le code pour appeler la méthode, émettez du code pour la stocker dans la variable locale `retVal` à l’aide de <xref:System.Reflection.Emit.OpCodes.Stloc_S>

    [!code-csharp[GenericMethodHowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#11)]
    [!code-vb[GenericMethodHowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#11)]

3. Émettez du code pour effectuer un cast du nouvel objet `TOutput` en `ICollection(Of TInput)` et le stocker dans la variable locale `ic`.

    [!code-csharp[GenericMethodHowTo#31](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#31)]
    [!code-vb[GenericMethodHowTo#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#31)]

4. Obtenez un <xref:System.Reflection.MethodInfo> représentant la méthode <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType>. Dans la mesure où la méthode agit sur `ICollection(Of TInput)` (`ICollection<TInput>` en C#), il est nécessaire d’obtenir la méthode `Add` propre à ce type construit. Vous ne pouvez pas utiliser la méthode <xref:System.Type.GetMethod%2A> pour obtenir ce <xref:System.Reflection.MethodInfo> directement à partir de `icollOfTInput`, car <xref:System.Type.GetMethod%2A> n’est pas pris en charge sur un type construit avec un <xref:System.Reflection.Emit.GenericTypeParameterBuilder>. Au lieu de cela, appelez <xref:System.Type.GetMethod%2A> sur `icoll`, qui contient la définition de type générique pour l’interface générique <xref:System.Collections.Generic.ICollection%601>. Utilisez ensuite la méthode <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29>`static` pour produire le <xref:System.Reflection.MethodInfo> pour le type construit. Le code suivant illustre cette méthode.

    [!code-csharp[GenericMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#12)]
    [!code-vb[GenericMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#12)]

5. Émettez le code pour initialiser la variable `index`, en chargeant un entier 0 32 bits et en le stockant dans la variable. Émettez du code pour créer une branche vers l’étiquette `enterLoop`. Cette étiquette n’a pas encore été marquée, car elle est à l’intérieur de la boucle. Le code de la boucle est émis à l’étape suivante.

    [!code-csharp[GenericMethodHowTo#32](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#32)]
    [!code-vb[GenericMethodHowTo#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#32)]

6. Émettez le code de la boucle. La première étape consiste à marquer le début de la boucle, en appelant <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> avec l’étiquette `loopAgain`. Les instructions de branche qui utilisent l’étiquette créent désormais une branche vers ce point du code. L’étape suivante consiste à effectuer un push de l’objet `TOutput`, casté en `ICollection(Of TInput)`, dans la pile. Il n’est pas nécessaire immédiatement, mais doit être en position d’appeler la méthode `Add`. Ensuite, le tableau d’entrée fait l’objet d’un push dans la pile, puis c’est au tour de la variable `index` qui contient l’index actuel dans le tableau. L’opcode <xref:System.Reflection.Emit.OpCodes.Ldelem> dépile l’index et le tableau et effectue un push de l’élément de tableau indexé dans la pile. La pile est maintenant prête pour l’appel à la méthode <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType>, qui dépile la collection et le nouvel élément et ajoute l’élément à la collection.

    Le reste du code dans la boucle incrémente l’index et vérifie si la boucle est finie : l’index et un entier 1 32 bits font l’objet d’un push dans la pile et sont additionnés, en laissant la somme dans la pile. La somme est stockée dans `index`. <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> est appelé pour définir ce point comme point d’entrée pour la boucle. L’index est de nouveau chargé. Le tableau d’entrée fait l’objet d’un push dans la pile et <xref:System.Reflection.Emit.OpCodes.Ldlen> est émis pour obtenir sa longueur. L’index et la longueur sont à présent dans la pile, et <xref:System.Reflection.Emit.OpCodes.Clt> est émis pour les comparer. Si l’index est inférieur à la longueur, <xref:System.Reflection.Emit.OpCodes.Brtrue_S> crée une nouvelle branche vers le début de la boucle.

    [!code-csharp[GenericMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#13)]
    [!code-vb[GenericMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#13)]

7. Émettez du code pour effectuer un push de l’objet `TOutput` dans la pile et obtenir un retour de la méthode. Les variables locales `retVal` et `ic` contiennent toutes deux des références au nouveau `TOutput` ; `ic` est utilisé uniquement pour accéder à la méthode <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType>.

    [!code-csharp[GenericMethodHowTo#33](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#33)]
    [!code-vb[GenericMethodHowTo#33](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#33)]

<a name="procedureSection2"></a>

### <a name="to-invoke-the-generic-method"></a>Pour appeler la méthode générique

1. `Factory` est une définition de méthode générique. Pour l’appeler, vous devez attribuer des types à ses paramètres de type générique. Pour ce faire, utilisez la méthode <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>. Le code suivant crée une méthode générique construite, en spécifiant <xref:System.String> pour `TInput` et `List(Of String)` (`List<string>` en C#) pour `TOutput`, et il affiche une représentation sous forme de chaîne de la méthode.

    [!code-csharp[GenericMethodHowTo#21](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#21)]
    [!code-vb[GenericMethodHowTo#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#21)]

2. Pour appeler la méthode avec liaison tardive, utilisez la méthode <xref:System.Reflection.MethodBase.Invoke%2A>. Le code suivant crée un tableau de <xref:System.Object> contenant pour seul élément un tableau de chaînes, et le passe en tant que liste d’arguments de la méthode générique. Le premier paramètre de <xref:System.Reflection.MethodBase.Invoke%2A> est une référence null car la méthode est `static`. La valeur de retour est castée en `List(Of String)` et son premier élément est affiché.

    [!code-csharp[GenericMethodHowTo#22](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#22)]
    [!code-vb[GenericMethodHowTo#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#22)]

3. Pour appeler la méthode à l’aide d’un délégué, vous devez avoir un délégué qui correspond à la signature de la méthode générique construite. Pour cela, une solution simple consiste à créer un délégué générique. Le code suivant crée une instance du délégué générique `D` défini dans l’exemple de code, à l’aide de la surcharge de méthode <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>, et appelle le délégué. Les délégués sont plus performants que les appels à liaison tardive.

    [!code-csharp[GenericMethodHowTo#23](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#23)]
    [!code-vb[GenericMethodHowTo#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#23)]

4. La méthode émise peut également être appelée à partir d’un programme qui fait référence à l’assembly enregistré.

## <a name="example"></a>Exemple

L’exemple de code suivant crée un type non générique, `DemoType`, avec une méthode générique, `Factory`. Cette méthode a deux paramètres de type générique, `TInput` pour spécifier un type d’entrée et `TOutput` pour spécifier un type de sortie. Pour implémenter `ICollection<TInput>` (`ICollection(Of TInput)` en Visual Basic), le paramètre de type `TOutput` a deux contraintes : être un type référence et avoir un constructeur sans paramètre.

La méthode a un paramètre formel, qui est un tableau de `TInput`. La méthode retourne une instance de `TOutput` qui contient tous les éléments du tableau d’entrée. `TOutput` peut être n’importe quel type de collection générique qui implémente l’interface générique <xref:System.Collections.Generic.ICollection%601>.

Quand le code est exécuté, l’assembly dynamique est enregistré en tant que DemoGenericMethod1.dll, et peut être examiné à l’aide de [Ildasm.exe (désassembleur IL)](../tools/ildasm-exe-il-disassembler.md).

> [!NOTE]
> Pour apprendre comment émettre du code, une méthode efficace consiste à écrire un programme Visual Basic, C# ou Visual C++ qui effectue la tâche que vous tentez d’émettre, et à utiliser le désassembleur pour examiner le code MSIL produit par le compilateur.

L’exemple de code inclut du code source équivalent à la méthode émise. La méthode émise est appelée avec liaison tardive, et également à l’aide d’un délégué générique déclaré dans l’exemple de code.

[!code-csharp[GenericMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#1)]
[!code-vb[GenericMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#1)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.Emit.MethodBuilder>
- [Procédure : définir un type générique avec l’émission de réflexion](how-to-define-a-generic-type-with-reflection-emit.md)
