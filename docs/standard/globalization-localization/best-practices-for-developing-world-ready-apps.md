---
title: Meilleures pratiques pour développer des applications mondialisables
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
ms.openlocfilehash: 9d9f6b3540bb04dd4af154fce2f91a3a7b6395ba
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555534"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Meilleures pratiques pour développer des applications internationales

Cette section décrit les meilleures pratiques pour développer des applications mondialisables.

## <a name="globalization-best-practices"></a>Meilleures pratiques de globalisation

1. Utilisez le codage Unicode en interne dans votre application.

2. Servez-vous des classes fournies par l'espace de noms <xref:System.Globalization> pour manipuler les données et les mettre en forme.

    - Pour trier, utilisez la classe <xref:System.Globalization.SortKey> et la classe <xref:System.Globalization.CompareInfo>.

    - Pour les comparaisons de chaînes, utilisez la classe <xref:System.Globalization.CompareInfo>.

    - Pour la mise en forme des dates et heures, utilisez la classe <xref:System.Globalization.DateTimeFormatInfo>.

    - Pour la mise en forme des nombres, utilisez la classe <xref:System.Globalization.NumberFormatInfo>.

    - Pour les calendriers grégoriens et non grégoriens, utilisez la classe <xref:System.Globalization.Calendar> ou l'une des implémentations de calendrier spécifiques.

3. Utilisez les paramètres de propriété de culture fournis par la classe <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> dans les situations appropriées. Utilisez la propriété <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> pour les tâches de mise en forme, par exemple la mise en forme des dates, des heures ou des nombres. Utilisez la propriété <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> pour récupérer des ressources. Notez que les propriétés `CurrentCulture` et `CurrentUICulture` peuvent être définies par thread.

4. Permettez à votre application de lire et d'écrire des données dans divers systèmes d'encodage à l'aide des classes d'encodage de l'espace de noms <xref:System.Text>. Ne supposez pas que les données entrées dans votre application seront par défaut codées en ASCII. Supposez que des caractères internationaux seront fournis partout où un utilisateur peut entrer un texte. Par exemple, l'application doit accepter les caractères internationaux dans les noms de serveurs, de répertoires, de fichiers et d'utilisateurs, ainsi que dans les URL.

5. Lorsque vous utilisez la classe <xref:System.Text.UTF8Encoding>, pour des raisons de sécurité, utilisez la fonctionnalité de détection d’erreurs offerte par cette classe. Pour activer la fonctionnalité de détection d’erreurs, créez une instance de la classe à l’aide du constructeur qui prend un paramètre `throwOnInvalidBytes` et affectez-lui la valeur `true`.

6. Autant que possible, traitez les chaînes comme des chaînes entières, et non comme une série de caractères. Ceci est particulièrement important lorsque vous effectuez un tri ou que vous recherchez des sous-chaînes. Vous éviterez ainsi les problèmes liés à l'analyse de caractères combinés. Vous pouvez aussi utiliser des unités de texte au lieu de caractères uniques avec la classe <xref:System.Globalization.StringInfo?displayProperty=nameWithType>.

7. Affichez le texte à l'aide des classes fournies par l'espace de noms <xref:System.Drawing>.

8. Pour préserver la cohérence parmi les divers systèmes d'exploitation, ne permettez pas aux paramètres utilisateur de se substituer à <xref:System.Globalization.CultureInfo>. Utilisez le constructeur `CultureInfo` qui accepte un paramètre `useUserOverride` et lui affecte la valeur `false`.

9. Testez les fonctionnalités de votre application sur des versions internationales des systèmes d'exploitation, en utilisant des données internationales.

10. Si une décision relative à la sécurité est basée sur le résultat d’une opération de comparaison de chaînes ou de changement de casse, utilisez une opération de chaînes indépendante de la culture. Cette pratique garantit que le résultat n'est pas affecté par la valeur de `CultureInfo.CurrentCulture`. Consultez la section [« comparaisons de chaînes qui utilisent la culture actuelle »](../base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) de [meilleures pratiques pour l’utilisation de chaînes](../base-types/best-practices-strings.md) pour obtenir un exemple qui montre comment les comparaisons de chaînes dépendantes de la culture peuvent produire des résultats incohérents.

## <a name="localization-best-practices"></a>Meilleures pratiques de localisation

1. Déplacez toutes les ressources localisables vers des bibliothèques DLL séparées, consacrées exclusivement à ces ressources. Les ressources localisables incluent les éléments d'interface utilisateur, tels que les chaînes, les messages d'erreur, les boîtes de dialogue et les menus, ainsi que les ressources d'objet incorporé.

2. Ne codez pas en dur les chaînes ou les ressources d'interface utilisateur.

3. Ne placez pas de ressources non localisables dans les DLL consacrées exclusivement aux ressources. Vous éviterez ainsi de compliquer la tâche des traducteurs.

4. N'utilisez pas de chaînes composites qui sont construites au moment de l'exécution à partir d'expressions concaténées. Les chaînes composites sont difficiles à localiser parce qu'elles supposent souvent un ordre grammatical anglais qui ne s'applique pas à toutes les langues.

5. Évitez les constructions ambigües telles que « Empty Folder », dans lesquelles les chaînes peuvent être traduites différemment selon les rôles grammaticaux de leurs composants. Par exemple, « empty » peut être un verbe ou un adjectif, ce qui conduit à des traductions différentes dans des langues telles que l'italien ou le français.

6. Évitez d'utiliser des images et des icônes qui contiennent du texte dans votre application. Le coût de leur localisation est élevé.

7. Prévoyez beaucoup de place pour la longueur des chaînes à développer dans l’interface utilisateur. Dans certaines langues, les phrases sont de 50 à 75 % plus longues que dans d'autres.

8. Utilisez la classe <xref:System.Resources.ResourceManager?displayProperty=nameWithType> pour récupérer des ressources selon culture.

9. Utilisez [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) pour créer des boîtes de dialogue Windows Forms, que vous pourrez localiser à l’aide de l’[Éditeur de ressources Windows Forms (Winres.exe)](../../framework/tools/winres-exe-windows-forms-resource-editor.md). Ne codez pas les boîtes de dialogue Windows Forms manuellement.

10. Confiez la localisation (la traduction) à des professionnels.

11. Vous trouverez une description complète de la création et de la localisation des ressources sur la page [Ressources dans les applications](../../framework/resources/index.md).

## <a name="globalization-best-practices-for-aspnet-applications"></a>Meilleures pratiques de globalisation pour les applications ASP.NET

1. Définissez explicitement les propriétés <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> et <xref:System.Globalization.CultureInfo.CurrentCulture%2A> dans vote application. Ne comptez pas sur leurs valeurs par défaut.

2. Notez que les applications ASP.NET sont des applications managées et, par conséquent, peuvent utiliser les mêmes classes que d'autres applications managées pour récupérer, afficher et manipuler des informations en fonction de la culture.

3. Gardez à l'esprit que vous pouvez spécifier les trois types d'encodage suivants dans ASP.NET :

    - requestEncoding spécifie l'encodage reçu du navigateur du client.

    - responseEncoding spécifie l'encodage à envoyer au navigateur du client. Dans la plupart des situations, cet encodage doit être identique à celui spécifié pour requestEncoding.

    - fileEncoding spécifie l'encodage par défaut pour l'analyse des fichiers .aspx, .asmx et .asax.

4. Spécifiez les valeurs des attributs requestEncoding, responseEncoding, fileEncoding, culture et uiCulture aux trois emplacements suivants dans une application ASP.NET :

    - Dans la section globalisation d'un fichier Web.config. Ce fichier est externe à l'application ASP.NET. Pour plus d’informations, consultez [ \<globalization> élément](/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100)).

    - Dans une directive de page. Notez que lorsqu'une application se trouve dans une page, le fichier a déjà été lu. De ce fait, il est trop tard pour spécifier fileEncoding et requestEncoding. Seuls uiCulture, Culture et responseEncoding peuvent être spécifiés dans une directive de page.

    - Par programme, dans le code de l'application. Ce paramètre peut varier par demande. Comme dans le cas de la directive de page, il est trop tard pour spécifier fileEncoding et requestEncoding au moment où le code de l'application est atteint. Seuls uiCulture, Culture et responseEncoding peuvent être spécifiés dans le code de l'application.

5. Notez que la valeur uiCulture peut être définie sur la langue acceptée par le navigateur.

## <a name="see-also"></a>Voir aussi

- [Globalisation et localisation](index.md)
- [Ressources dans les applications de bureau](../../framework/resources/index.md)
