---
ms.openlocfilehash: 0237c848d71150aaea1f9de4f4b16a0cbbc4ab3a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615665"
---
### <a name="new-64-bit-jit-compiler-in-the-net-framework-46"></a>Nouveau compilateur JIT 64 bits dans .NET Framework 4.6

#### <a name="details"></a>Détails

À compter du .NET Framework 4.6, un nouveau compilateur JIT 64 bits est utilisé pour la compilation juste-à-temps. Dans certains cas, une exception inattendue est levée ou un comportement différent de celui obtenu quand l’application utilise le compilateur 32 bits ou le compilateur JIT 64 bits plus ancien est observé. Cette modification n’affecte pas le compilateur JIT 32 bits. Voici quelques-unes des différences connues :

- Dans certaines conditions, une opération d’unboxing peut lever une <xref:System.NullReferenceException> dans les versions Release avec l’optimisation activée.
- Dans certains cas, l’exécution du code de production dans un corps de méthode volumineux peut lever une <xref:System.StackOverflowException>.
- Dans certaines conditions, les structures passées à une méthode sont traitées comme des types référence plutôt que comme des types valeur dans les versions Release. Ce problème se manifeste notamment lorsque des éléments dans une collection apparaissent dans un ordre inattendu.
- Dans certaines conditions, la comparaison de valeurs <xref:System.UInt16> avec le bit le plus élevé est incorrecte si l’optimisation est activée.
- Sous certaines conditions, en particulier lors de l’initialisation de tableaux de valeurs, l’initialisation de la mémoire par l’instruction <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> du langage intermédiaire peut initialiser la mémoire avec une valeur incorrecte. Cela peut entraîner une exception non gérée ou une sortie incorrecte.
- Dans certains cas rares, un test conditionnel binaire peut retourner une valeur <xref:System.Boolean> incorrecte ou lever une exception si les optimisations du compilateur sont activées.
- Sous certaines conditions, si une instruction `if` est utilisée pour tester une condition avant d’entrer dans un bloc `try` et dans la sortie du bloc `try`, et que la même condition est évaluée dans le bloc `catch` ou `finally`, le nouveau compilateur JIT 64 bits supprime la condition `if` du bloc `catch` ou `finally` lorsqu’il optimise le code. Par conséquent, le code à l’intérieur de l’instruction `if` dans le bloc `catch` ou `finally` est exécuté de manière non conditionnelle.

#### <a name="suggestion"></a>Suggestion

**Atténuation des problèmes connus** <br/> Si vous rencontrez les problèmes répertoriés ci-dessus, vous pouvez les traiter en procédant d’une des façons suivantes :

- Mettez à niveau vers .NET Framework 4.6.2. Le nouveau compilateur 64 bits inclus avec .NET Framework 4.6.2 résout chacun de ces problèmes connus.
- Assurez-vous que votre version de Windows est à jour en exécutant Windows Update. Les mises à jour de service pour .NET Framework 4.6 et 4.6.1 corrigent chacun de ces problèmes, à l’exception de <xref:System.NullReferenceException> dans une opération d’unboxing.
- Compilez avec l’ancien compilateur JIT 64 bits. Consultez la section **Atténuation des autres problèmes** pour plus d’informations sur cette procédure.
**Atténuation des autres problèmes** <br/> Si vous rencontrez une autre différence de comportement entre le code compilé avec l’ancien compilateur JIT 64 bits et celui compilé avec le nouveau compilateur, ou entre les versions Debug et Release de votre application lorsque les deux sont compilées avec le nouveau compilateur JIT 64 bits, vous pouvez procéder comme suit pour compiler votre application avec l’ancien compilateur JIT 64 bits :

- Pour chaque application, vous pouvez ajouter l' [<](~/docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md) élément au fichier de configuration de votre application. Ce qui suit désactive la compilation avec le nouveau compilateur JIT 64 bits et utilise l’ancien compilateur à la place.

    ```xml
    <?xml version ="1.0"?>
    <configuration>
      <runtime>
       <useLegacyJit enabled="1" />
      </runtime>
    </configuration>
    ```

- Pour chaque utilisateur concerné, vous pouvez ajouter une valeur `REG_DWORD` nommée `useLegacyJit` à la clé de registre `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`. La valeur 1 active l’ancien compilateur JIT 64 bits ; la valeur 0 le désactive et active le nouveau compilateur JIT 64 bits.
- Pour chaque machine concernée, vous pouvez ajouter une valeur `REG_DWORD` nommée `useLegacyJit` à la clé de registre `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`. La valeur `1` active l’ancien compilateur JIT 64 bits ; la valeur `0` le désactive et active le nouveau compilateur JIT 64 bits.
Vous pouvez également nous indiquer votre problème en signalant un bogue sur [Microsoft Connect](https://connect.microsoft.com/VisualStudio).

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6         |
| Type    | Reciblage |
