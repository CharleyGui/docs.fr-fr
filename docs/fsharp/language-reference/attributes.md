---
title: Attributs
description: Découvrez comment F# les attributs permettent d’appliquer des métadonnées à une construction de programmation.
ms.date: 02/19/2020
ms.openlocfilehash: 77b84713ab9360166b3634d406993cf209c8a623
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543636"
---
# <a name="attributes"></a>Attributs

Les attributs permettent d’appliquer des métadonnées à une construction de programmation.

## <a name="syntax"></a>Syntaxe

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>Notes

Dans la syntaxe précédente, la *cible* est facultative et, si elle est présente, spécifie le genre d’entité de programme à laquelle l’attribut s’applique. Les valeurs valides pour la *cible* sont indiquées dans le tableau qui apparaît plus loin dans ce document.

L' *attribut-Name* fait référence au nom (éventuellement qualifié avec des espaces de noms) d’un type d’attribut valide, avec ou sans le suffixe `Attribute` qui est généralement utilisé dans les noms de types d’attributs. Par exemple, le type `ObsoleteAttribute` peut être abrégé en `Obsolete` dans ce contexte.

Les *arguments* sont les arguments du constructeur pour le type d’attribut. Si un attribut a un constructeur sans paramètre, la liste d’arguments et les parenthèses peuvent être omises. Les attributs prennent en charge les arguments positionnels et les arguments nommés. Les *arguments positionnels* sont des arguments utilisés dans l’ordre dans lequel ils apparaissent. Les arguments nommés peuvent être utilisés si l’attribut a des propriétés publiques. Vous pouvez les définir à l’aide de la syntaxe suivante dans la liste d’arguments.

```fsharp
property-name = property-value
```

Ces initialisations de propriété peuvent être dans n’importe quel ordre, mais elles doivent suivre tous les arguments positionnels. Voici un exemple d’un attribut qui utilise des arguments positionnels et des initialisations de propriétés :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

Dans cet exemple, l’attribut est `DllImportAttribute`, ici utilisé sous forme abrégée. Le premier argument est un paramètre positionnel et le second est une propriété.

Les attributs sont une construction de programmation .NET qui permet à un objet connu comme un *attribut* d’être associé à un type ou à un autre élément de programme. L’élément de programme auquel un attribut est appliqué est appelé la *cible d’attribut*. L’attribut contient généralement des métadonnées sur sa cible. Dans ce contexte, les métadonnées peuvent être des données relatives au type autres que ses champs et membres.

Les attributs F# dans peuvent être appliqués aux constructions de programmation suivantes : fonctions, méthodes, assemblys, modules, types (classes, enregistrements, structures, interfaces, délégués, énumérations, unions, etc.), constructeurs, propriétés, champs, paramètres, paramètres de type et valeurs de retour. Les attributs ne sont pas autorisés sur les liaisons `let` dans des classes, des expressions ou des expressions de flux de travail.

En règle générale, la déclaration d’attribut apparaît directement avant la déclaration de la cible de l’attribut. Plusieurs déclarations d’attribut peuvent être utilisées ensemble, comme suit :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

Vous pouvez interroger des attributs au moment de l’exécution à l’aide de la réflexion .NET.

Vous pouvez déclarer plusieurs attributs individuellement, comme dans l’exemple de code précédent, ou vous pouvez les déclarer dans un jeu de crochets si vous utilisez un point-virgule pour séparer les attributs et les constructeurs individuels, comme suit :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

Les attributs généralement rencontrés incluent l’attribut `Obsolete`, les attributs pour les considérations de sécurité, les attributs pour la prise en charge de COM, les attributs liés à la propriété du code et les attributs indiquant si un type peut être sérialisé. L’exemple suivant illustre l’utilisation de l’attribut `Obsolete`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

Pour les cibles d’attribut `assembly` et `module`, vous appliquez les attributs à une liaison de `do` de niveau supérieur dans votre assembly. Vous pouvez inclure le mot `assembly` ou `module` dans la déclaration d’attribut, comme suit :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

Si vous omettez la cible d’attribut pour un attribut appliqué à une liaison de `do` F# , le compilateur tente de déterminer la cible d’attribut qui est logique pour cet attribut. De nombreuses classes d’attributs ont un attribut de type `System.AttributeUsageAttribute` qui contient des informations sur les cibles possibles prises en charge pour cet attribut. Si le `System.AttributeUsageAttribute` indique que l’attribut prend en charge les fonctions en tant que cibles, l’attribut est pris pour s’appliquer au point d’entrée principal du programme. Si le `System.AttributeUsageAttribute` indique que l’attribut prend en charge les assemblys en tant que cibles, le compilateur prend l’attribut à appliquer à l’assembly. La plupart des attributs ne s’appliquent pas aux fonctions et aux assemblys, mais dans les cas où ils le font, l’attribut est pris pour s’appliquer à la fonction principale du programme. Si la cible de l’attribut est spécifiée explicitement, l’attribut est appliqué à la cible spécifiée.

Bien qu’il ne soit généralement pas nécessaire de spécifier explicitement la cible de l’attribut, les valeurs valides pour *target* dans un attribut, ainsi que des exemples d’utilisation, sont indiquées dans le tableau suivant :

<table>
  <tr>
    <th>Cible d’attribut</td>
    <th>Exemple</td>
  </tr>
  <tr>
    <td>assembly</td>
    <td><pre><code class="lang-fsharp">[&lt;assembly: AssemblyVersion("1.0.0.0")&gt;]</code></pre></td>
  </tr>
  <tr>
    <td>return</td>
    <td><pre><code class="lang-fsharp">let function1 x : [&lt;return: MyCustomAttributeThatWorksOnReturns&gt;] int = x + 1</code></pre></td>
  </tr>
  <tr>
    <td>field</td>
    <td><pre><code class="lang-fsharp">[&lt;DefaultValue&gt;] val mutable x: int</code></pre></td>
  </tr>
  <tr>
    <td>propriété</td>
    <td><pre><code class="lang-fsharp">[&lt;Obsolete&gt;] this.MyProperty = x</code></pre></td>
  </tr>
  <tr>
    <td>param</td>
    <td><pre><code class="lang-fsharp">member this.MyMethod([&lt;Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td>
  </tr>
  <tr>
    <td>type</td>
    <td>
        <pre><code class="lang-fsharp">
[&lt;type: StructLayout(LayoutKind.Sequential)&gt;]
type MyStruct =
  struct
    val x : byte
    val y : int
  end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F#](index.md)
