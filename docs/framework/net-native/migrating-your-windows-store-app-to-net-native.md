---
title: Migration de votre application du Windows Store vers .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 987669fc51eeaf7e3bdef3e91a2f1ce23164a055
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81389700"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a>Migrer votre application du Windows Store vers .NET Native

.NET Native fournit une compilation statique des applications dans le Windows Store ou sur l’ordinateur du développeur. Cela diffère de la compilation dynamique effectuée pour les applications du Windows Store par le compilateur juste-à-temps (JIT) ou le [générateur d'images natives (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) sur l'appareil. Malgré les différences, .NET Native tente de maintenir la compatibilité avec [.net pour les applications du Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29). Pour l’essentiel, les éléments qui fonctionnent sur .NET pour les applications du Windows Store fonctionnent également avec .NET Native.  Toutefois, dans certains cas, vous pouvez rencontrer des changements de comportement. Ce document traite de ces différences entre le .NET standard pour les applications du Windows Store et .NET Native dans les domaines suivants :

- [Différences générales au moment de l'exécution](#Runtime)

- [Différences de programmation dynamique](#Dynamic)

- [Autres différences en matière de réflexion](#Reflection)

- [API et scénarios non pris en charge](#Unsupported)

- [Différences concernant Visual Studio](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a>Différences générales au moment de l'exécution

- Les exceptions, telles que <xref:System.TypeLoadException> , qui sont levées par le compilateur JIT quand une application s’exécute sur le Common Language Runtime (CLR) entraînent généralement des erreurs au moment de la compilation lorsqu’elles sont traitées par .net native.

- N'appelez pas la méthode <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> à partir du thread d'interface utilisateur d'une application. Cela peut entraîner un blocage sur .NET Native.

- Ne vous fiez pas à l'ordre d'appel des constructeurs de classe statique. Dans .NET Native, l’ordre d’appel est différent de l’ordre sur le runtime standard. (Même avec le runtime standard, évitez de vous fier à l'ordre d'exécution des constructeurs de classe statique.)

- Des boucles infinies sans appel (par exemple, `while(true);`) sur n'importe quel thread peuvent entraîner l'arrêt de l'application. Il en va de même dans le cas des attentes de longues durées ou infinies.

- Certains cycles d’initialisation générique ne lèvent pas d’exceptions dans .NET Native. Par exemple, le code suivant lève une exception <xref:System.TypeLoadException> sur le CLR standard, Dans .NET Native, cela ne l’est pas.

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- Dans certains cas, .NET Native fournit différentes implémentations de .NET Framework bibliothèques de classes. Un objet retourné par une méthode implémente toujours les membres du type retourné. Toutefois, l'implémentation de sa sauvegarde étant différente, vous ne pourrez peut-être pas effectuer un cast vers le même ensemble de types comme vous le pourriez sur d'autres plateformes .NET Framework. Par exemple, dans certains cas, vous ne pourrez peut-être pas effectuer un cast de l'objet d'interface <xref:System.Collections.Generic.IEnumerable%601> retourné par des méthodes telles que <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> ou <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> vers `T[]`.

- Le cache WinInet n’est pas activé par défaut sur .NET pour les applications du Windows Store, mais il se trouve sur .NET Native. Cela améliore les performances, mais a des implications pour les jeux de travail. Aucune action n'est nécessaire de la part du développeur.

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a>Différences de programmation dynamique

.NET Native des liens statiques dans le code à partir du .NET Framework pour que l’application de code soit locale pour des performances maximales. Cependant, la taille des binaires doit demeurer petite, pour que l'ensemble du .NET Framework ne soit pas sollicité. Le compilateur .NET Native résout cette limitation en utilisant un réducteur de dépendances qui supprime les références au code inutilisé. Toutefois, .NET Native peut ne pas conserver ou générer des informations de type et du code quand ces informations ne peuvent pas être déduites statiquement au moment de la compilation, mais qu’elles sont récupérées dynamiquement au moment de l’exécution.

.NET Native active la réflexion et la programmation dynamique. Toutefois, tous les types ne peuvent pas être marqués pour réflexion, car la taille du code généré serait alors trop grande (notamment car la réflexion d'API publiques dans le .NET Framework est prise en charge). Le compilateur .NET Native permet de choisir intelligemment les types devant prendre en charge la réflexion, et il conserve les métadonnées et génère le code uniquement pour ces types.

Par exemple, pour la liaison de données, une application doit pouvoir mapper les noms de propriété sur les fonctions. Dans .NET pour les applications du Windows Store, le Common Language Runtime utilise automatiquement la réflexion pour fournir cette fonctionnalité pour les types managés et les types natifs disponibles publiquement. Dans .NET Native, le compilateur comprend automatiquement les métadonnées des types auxquels vous liez des données.

Le compilateur .NET Native peut également gérer les types génériques couramment utilisés tels que <xref:System.Collections.Generic.List%601> et <xref:System.Collections.Generic.Dictionary%602> , qui fonctionnent sans nécessiter d’indicateurs ou de directives. Le mot clé [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) est également pris en charge, dans certaines limites.

> [!NOTE]
> Vous devez tester minutieusement tous les chemins de code dynamiques quand vous portez votre application sur .NET Native.

La configuration par défaut de .NET Native est suffisante pour la plupart des développeurs, mais certains développeurs peuvent souhaiter ajuster leurs configurations à l’aide d’un fichier de directives Runtime (. rd. Xml). En outre, dans certains cas, le compilateur .NET Native n’est pas en mesure de déterminer les métadonnées qui doivent être disponibles pour la réflexion et s’appuie sur les indicateurs, notamment dans les cas suivants :

- Certaines constructions telles que <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> et <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> ne peuvent pas être déterminées de manière statique.

- Comme le compilateur ne peut pas déterminer les instanciations, un type générique à réfléchir doit être spécifié par les directives runtime. Cela est nécessaire à double titre : tout le code doit être inclus, et la réflexion de types génériques peut former un cycle infini (par exemple, quand une méthode générique est appelée sur un type générique).

> [!NOTE]
> Les directives runtime sont définies dans un fichier de directives runtime (.rd.xml). Pour obtenir des informations générales sur l’utilisation de ce fichier, consultez la rubrique [Bien démarrer](getting-started-with-net-native.md). Pour plus d’informations sur les directives runtime, consultez [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).

.NET Native comprend également des outils de profilage qui permettent au développeur de déterminer quels types en dehors du jeu par défaut doivent prendre en charge la réflexion.

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a>Autres différences en matière de réflexion

Il existe un certain nombre d’autres différences de comportement liées à la réflexion entre le .NET pour les applications du Windows Store et les .NET Native.

Dans .NET Native :

- La réflexion privée de types et de membres de la bibliothèque de classes .NET Framework n'est pas prise en charge. Vous pouvez, toutefois, réfléchir vos propres types et membres privés, ainsi que les types et les membres dans des bibliothèques tierces.

- La propriété <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> retourne correctement `false` pour un objet <xref:System.Reflection.ParameterInfo> qui représente une valeur de retour. Dans .NET pour les applications du Windows Store, elle retourne `true`. Le langage intermédiaire ne prend pas cela en charge directement et l'interprétation est laissée au langage.

- Les membres publics sur les structures <xref:System.RuntimeFieldHandle> et <xref:System.RuntimeMethodHandle> ne sont pas pris en charge. Ces types sont pris en charge uniquement pour LINQ, les arborescences d'expression et l'initialisation de tableau statique.

- <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> et <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> comprennent des membres masqués dans des classes de base et peuvent donc être remplacés sans substitutions explicites. Cela vaut également pour les autres méthodes [RuntimeReflectionExtensions.GetRuntime*](xref:System.Reflection.RuntimeReflectionExtensions) .

- <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>et <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> n’échouent pas lorsque vous essayez de créer certaines combinaisons (par exemple, un tableau d' `byref` objets).

- Vous ne pouvez pas utiliser la réflexion pour appeler des membres qui ont des paramètres de pointeur.

- Vous ne pouvez pas utiliser la réflexion pour obtenir ou définir un champ de pointeur.

- Lorsque le nombre d’arguments est incorrect et que le type de l’un des arguments est incorrect, .NET Native lève une exception <xref:System.ArgumentException> au lieu d’un <xref:System.Reflection.TargetParameterCountException> .

- La sérialisation binaire des exceptions n'est généralement pas prise en charge. Ainsi, les objets non sérialisables peuvent être ajoutés au dictionnaire <xref:System.Exception.Data%2A?displayProperty=nameWithType> .

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a>API et scénarios non pris en charge

Les sections suivantes répertorient les API et les scénarios non pris en charge pour le développement général, l'interopérabilité et les technologies telles que HTTPClient et Windows Communication Foundation (WCF) :

- [Développement général](#General)

- [HttpClient](#HttpClient)

- [Interop](#Interop)

- [API non prises en charge](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a>Différences de développement général

**Types de valeur**

- Si vous substituez les méthodes <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> et <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> pour un type de valeur, n'appelez pas les implémentations de classe de base. Dans .NET pour les applications du Windows Store, ces méthodes reposent sur la réflexion. Au moment de la compilation, .NET Native génère une implémentation qui ne repose pas sur la réflexion du Runtime. Cela signifie que si vous ne substituez pas ces deux méthodes, elles fonctionneront comme prévu, car .NET Native génère l’implémentation au moment de la compilation. Toutefois, la substitution de ces méthodes tout en appelant l'implémentation de la classe de base entraîne une exception.

- Les types de valeur supérieurs à 1 mégaoctet ne sont pas pris en charge.

- Les types valeur ne peuvent pas avoir de constructeur sans paramètre dans .NET Native. (C# et Visual Basic interdisent les constructeurs sans paramètre sur les types valeur. Toutefois, ceux-ci peuvent être créés dans un langage intermédiaire.)

**Tableaux**

- Les tableaux présentant une limite inférieure différente de zéro ne sont pas pris en charge. En règle générale, ces tableaux sont créés en appelant la surcharge <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> .

- La création dynamique de tableaux multidimensionnels n'est pas prise en charge. Ces tableaux sont généralement créés en appelant une surcharge de la méthode <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> qui inclut un paramètre `lengths` , ou en appelant la méthode <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> .

- Les tableaux multidimensionnels qui ont quatre dimensions ou plus ne sont pas pris en charge ; il s'agit de tableaux dont la propriété <xref:System.Array.Rank%2A?displayProperty=nameWithType> à une valeur supérieure ou égale à quatre. Utilisez des [tableaux en escalier](../../csharp/programming-guide/arrays/jagged-arrays.md) (tableaux de tableaux) à la place. Par exemple, `array[x,y,z]` n'est pas valide, contrairement à `array[x][y][z]` .

- L'écart entre les tableaux multidimensionnels n'est pas pris en charge et provoque une exception <xref:System.InvalidCastException> au moment de l'exécution.

**Génériques**

- Une extension de type générique infinie entraîne une erreur du compilateur. Par exemple, la compilation de ce code échoue :

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

**Pointeurs**

- Les tableaux de pointeurs ne sont pas pris en charge.

- Vous ne pouvez pas utiliser la réflexion pour obtenir ou définir un champ de pointeur.

**Sérialisation**

L'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> n'est pas pris en charge. Utilisez plutôt l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> .

**Ressources**

L'utilisation de ressources localisées avec la classe <xref:System.Diagnostics.Tracing.EventSource> n'est pas prise en charge. La propriété <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> ne définit pas de ressources localisées.

**Délégués**

`Delegate.BeginInvoke` et `Delegate.EndInvoke` ne sont pas pris en charge.

**API diverses**

- La propriété [TypeInfo. Guid](xref:System.Type.GUID) lève une <xref:System.PlatformNotSupportedException> exception si un <xref:System.Runtime.InteropServices.GuidAttribute> attribut n’est pas appliqué au type. Le GUID est utilisé principalement pour la prise en charge de COM.

- La <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> méthode analyse correctement les chaînes qui contiennent des dates courtes dans .net native. Toutefois, elle n’assure pas la compatibilité avec les changements apportés à l’analyse des dates et heures, décrits dans les articles de la Base de connaissances Microsoft [KB2803771](https://support.microsoft.com/kb/2803771) et [KB2803755](https://support.microsoft.com/kb/2803755).

- <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")`est correctement arrondi dans .net native. Dans certaines versions du CLR, la chaîne de résultat est tronquée et non arrondie.

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a>Différences pour HttpClient

Dans .NET Native, la <xref:System.Net.Http.HttpClientHandler> classe utilise en interne WinINet (via la <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> classe) au lieu des <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> classes et utilisées dans le .NET standard pour les applications du Windows Store.  WinINet ne prend pas en charge toutes les options de configuration prises en charge par la classe <xref:System.Net.Http.HttpClientHandler> .  Par conséquent :

- Certaines des propriétés de fonctionnalité lors du <xref:System.Net.Http.HttpClientHandler> retour `false` sur .net native, alors qu’elles retournent `true` dans le .NET standard pour les applications du Windows Store.

- Certains accesseurs de propriété de configuration `get` retournent toujours une valeur fixe sur .net native qui est différente de la valeur configurable par défaut dans .net pour les applications du Windows Store.

Certaines différences de comportement supplémentaires sont décrites dans les sous-sections suivantes.

**Proxy**

La <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> classe ne prend pas en charge la configuration ou la substitution du proxy en fonction de la demande.  Cela signifie que toutes les demandes sur .NET Native utilisent le serveur proxy configuré par le système ou aucun serveur proxy, en fonction de la valeur de la <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> propriété.  Dans .NET pour les applications du Windows Store, le serveur proxy est défini par la propriété <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> .  Sur .NET Native, l’affectation <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> d’une valeur autre que `null` lève une <xref:System.PlatformNotSupportedException> exception.  La <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> propriété retourne `false` sur .net native, alors qu’elle retourne `true` dans le .NET Framework standard pour les applications du Windows Store.

**Redirection automatique**

La <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> classe n’autorise pas la configuration du nombre maximal de redirections automatiques.  La valeur de la propriété <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> est 50 par défaut dans la version .NET standard pour les applications du Windows Store et peut être modifiée. Sur .NET Native, la valeur de cette propriété est 10 et la tentative de modification lève une <xref:System.PlatformNotSupportedException> exception.  La <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> propriété retourne `false` sur .net native, alors qu’elle retourne `true` dans .net pour les applications du Windows Store.

**Décompression automatique**

.NET pour les applications du Windows Store vous permet de définir la propriété <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> sur <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, à la fois sur <xref:System.Net.DecompressionMethods.Deflate> et <xref:System.Net.DecompressionMethods.GZip>, ou sur <xref:System.Net.DecompressionMethods.None>.  .NET Native ne prend en charge que <xref:System.Net.DecompressionMethods.Deflate> avec <xref:System.Net.DecompressionMethods.GZip> , ou <xref:System.Net.DecompressionMethods.None> .  Si vous essayez de définir la propriété <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> uniquement sur <xref:System.Net.DecompressionMethods.Deflate> ou <xref:System.Net.DecompressionMethods.GZip> , elle est automatiquement définie à la fois sur <xref:System.Net.DecompressionMethods.Deflate> et <xref:System.Net.DecompressionMethods.GZip>.

**Internes**

La gestion des cookies est effectuée simultanément par <xref:System.Net.Http.HttpClient> et WinINet.  Les cookies de <xref:System.Net.CookieContainer> sont combinés aux cookies du cache de cookies WinINet.  La suppression d'un cookie de <xref:System.Net.CookieContainer> empêche <xref:System.Net.Http.HttpClient> de l'envoyer, mais si le cookie a déjà été vu par WinINet et que les cookies n'ont pas été supprimés par l'utilisateur, WinInet l'envoie.  Il est impossible de supprimer par programmation un cookie de WinINet à l'aide de l'API <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>ou <xref:System.Net.CookieContainer> .  Définir la propriété <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> sur `false` entraîne uniquement l'arrêt de l'envoi des cookies par <xref:System.Net.Http.HttpClient> ; WinINet peut toujours inclure ses cookies dans la demande.

**Informations d'identification**

Dans .NET pour les applications du Windows Store, les propriétés <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> et <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> fonctionnent de manière indépendante.  En outre, la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> accepte tout objet qui implémente l'interface <xref:System.Net.ICredentials> .  Dans .NET Native, l’affectation de la valeur à la <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> propriété `true` entraîne l’activation <xref:System.Net.Http.HttpClientHandler.Credentials%2A> de la propriété `null` .  En outre, la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> peut être définie uniquement sur `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>ou un objet de type <xref:System.Net.NetworkCredential>.  L'affectation de tout autre objet <xref:System.Net.ICredentials> , le plus courant étant <xref:System.Net.CredentialCache>, à la propriété <xref:System.Net.Http.HttpClientHandler.Credentials%2A> lève une <xref:System.PlatformNotSupportedException>.

**Autres fonctionnalités non prises en charge ou non configurables**

Dans .NET Native :

- La valeur de la propriété <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> est toujours <xref:System.Net.Http.ClientCertificateOption.Automatic>.  Dans .NET pour les applications du Windows Store, la valeur par défaut est <xref:System.Net.Http.ClientCertificateOption.Manual>.

- La propriété <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> n'est pas configurable.

- La propriété <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> a toujours la valeur `true`.  Dans .NET pour les applications du Windows Store, la valeur par défaut est `false`.

- L'en-tête `SetCookie2` dans les réponses est ignoré, car considéré comme obsolète.

<a name="Interop"></a>
### <a name="interop-differences"></a>Différences concernant l'interopérabilité
 **API déconseillées**

 Un certain nombre d'API peu utilisées pour l'interopérabilité avec du code managé ont été déconseillées. En cas d’utilisation avec .NET Native, ces API peuvent lever une <xref:System.NotImplementedException> <xref:System.PlatformNotSupportedException> exception ou, ou entraîner une erreur du compilateur. Dans .NET pour les applications du Windows Store, ces API sont marquées comme obsolètes, même si les appeler génère un avertissement, plutôt qu'une erreur, du compilateur.

 Les API déconseillées pour le `VARIANT` marshaling sont les suivantes :

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>est pris en charge, mais lève une exception dans certains scénarios, par exemple quand il est utilisé avec [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) ou des `byref` variants.

 Les API déconseillées pour la prise en charge [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) incluent :

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

Les API déconseillées pour les événements COM classiques sont les suivantes :

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

Les API déconseillées dans l' <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, qui ne sont pas prises en charge dans .net native, incluent :

- <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>(tous les membres)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>(tous les membres)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>(tous les membres)
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

Les autres fonctionnalités d’interopérabilité non prises en charge sont les suivantes :

- <xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>(tous les membres)
- <xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>(tous les membres)
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 API de marshaling rarement utilisées :

- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>

 **Appel de plateforme et compatibilité avec l'interopérabilité COM**

 La plupart des scénarios d’appel de code non managé et de COM Interop sont toujours pris en charge dans .NET Native. En particulier, toute l'interopérabilité avec les API Windows Runtime (WinRT) et tout le marshaling nécessaire pour le Windows Runtime sont pris en charge. Cela inclut la prise en charge du marshaling pour les éléments suivants :

- Tableaux (y compris <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)

- `BStr`

- Délégués

- Chaînes (Unicode, Ansi et HSTRING)

- Structures (`byref` et `byval`)

- Unions

- Handles Win32

- Toutes les constructions WinRT

- Prise en charge partielle du marshaling des types variant. Les constructions suivantes sont admises :

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

Toutefois, .NET Native ne prend pas en charge les éléments suivants :

- L'utilisation d'événements COM classiques

- La mise en œuvre de l'interface <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> sur un type managé

- L’implémentation de l’interface [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) sur un type managé via l’attribut <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> . Toutefois, vous ne pouvez pas appeler des objets COM via `IDispatch` , et votre objet managé ne peut pas implémenter `IDispatch` .

Utiliser la réflexion pour appeler une méthode d'appel de plateforme n'est pas pris en charge. Vous pouvez contourner cette limitation en encapsulant l'appel de méthode dans une autre méthode et en utilisant la réflexion pour appeler le wrapper.

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>Autres différences par rapport aux API .NET pour les applications du Windows Store

Cette section répertorie les API restantes qui ne sont pas prises en charge dans .NET Native. Le plus grand ensemble d’API non prises en charge est l’API Windows Communication Foundation (WCF).

**DataAnnotations (System.ComponentModel.DataAnnotations)**

Les types dans les <xref:System.ComponentModel.DataAnnotations> <xref:System.ComponentModel.DataAnnotations.Schema> espaces de noms et ne sont pas pris en charge dans .net native. Celles-ci incluent les types suivants qui sont présents dans .NET pour les applications du Windows Store pour Windows 8 :

- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>

 **Visual Basic**

Visual Basic n’est actuellement pas pris en charge dans .NET Native. Les types suivants dans les <xref:Microsoft.VisualBasic> <xref:Microsoft.VisualBasic.CompilerServices> espaces de noms et ne sont pas disponibles dans .net Native :

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>

**Contexte de réflexion (espace de noms System.Reflection.Context)**

La <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> classe n’est pas prise en charge dans .net native.

**RTC (System.Net.Http.Rtc)**

La `System.Net.Http.RtcRequestFactory` classe n’est pas prise en charge dans .net native.

**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**

Les types des [espaces de noms System. ServiceModel. *](xref:System.ServiceModel) ne sont pas pris en charge dans .net native. Il s’agit notamment des types suivants :

- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>

### <a name="differences-in-serializers"></a>Différences entre les sérialiseurs

Les différences suivantes concernent la sérialisation et la désérialisation avec les classes <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>et <xref:System.Xml.Serialization.XmlSerializer> :

- Dans .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ne parviennent pas à sérialiser ou désérialiser une classe dérivée qui a un membre de classe de base dont le type n’est pas un type de sérialisation racine. Par exemple, dans le code suivant, sérialiser ou désérialiser `Y` génère une erreur :

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  Le type `InnerType` n'est pas connu du sérialiseur, car les membres de la classe de base ne sont pas parcourus pendant la sérialisation.

- <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ne parviennent pas à sérialiser une classe ou une structure qui implémente l'interface <xref:System.Collections.Generic.IEnumerable%601> . Par exemple, les types suivants ne parviennent pas à sérialiser ou à désérialiser :

- <xref:System.Xml.Serialization.XmlSerializer> ne sérialise pas la valeur d'objet suivante, car il ne connaît pas le type exact de l'objet à sérialiser :

- <xref:System.Xml.Serialization.XmlSerializer> ne parvient pas à sérialiser ou à désérialiser si le type de l'objet sérialisé est <xref:System.Xml.XmlQualifiedName>.

- Tous les sérialiseurs (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>et <xref:System.Xml.Serialization.XmlSerializer>) ne parviennent pas à générer un code de sérialisation pour un type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> ou pour un type contenant <xref:System.Xml.Linq.XElement>. Ils affichent des erreurs de génération à la place.

- Les constructeurs suivants des types de sérialisation ne fonctionnent pas nécessairement comme prévu :

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29>

- <xref:System.Xml.Serialization.XmlSerializer> ne parvient pas à générer le code pour un type dont les méthodes possèdent un des attributs suivants :

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <xref:System.Xml.Serialization.XmlSerializer> ne traite pas l'interface de sérialisation personnalisée <xref:System.Xml.Serialization.IXmlSerializable> . Si vous avez une classe qui implémente cette interface, <xref:System.Xml.Serialization.XmlSerializer> considère le type comme un ancien objet CLR simple et sérialise uniquement ses propriétés publiques.

- La sérialisation d’un <xref:System.Exception> objet brut ne fonctionne pas correctement avec <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .

<a name="VS"></a>

## <a name="visual-studio-differences"></a>Différences concernant Visual Studio

**Exceptions et débogage**

Quand vous exécutez des applications compilées à l’aide de .NET Native dans le débogueur, les exceptions de première chance sont activées pour les types d’exception suivants :

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

**Génération d'applications**

Recourez aux outils de génération x86 qui sont utilisés par défaut par Visual Studio. Nous vous déconseillons d'utiliser les outils MSBuild AMD64, qui se trouvent dans C:\Program Files (x86)\MSBuild\12.0\bin\amd64, car ils peuvent créer des problèmes de génération.

**Profileurs**

- Le profileur d'UC Visual Studio et le profileur de mémoire XAML n'affichent pas Uniquement mon code correctement.

- Le profileur de mémoire XAML n'affiche pas avec précision les données du tas managé.

- Le profileur d'UC ne peut pas identifier correctement les modules, et affiche les noms de fonction avec préfixe.

**Projets de bibliothèque de tests unitaires**

L’activation de .NET Native sur une bibliothèque de tests unitaires pour un projet d’applications du Windows Store n’est pas prise en charge et entraîne l’échec de la génération du projet.

## <a name="see-also"></a>Voir aussi

- [Prise en main](getting-started-with-net-native.md)
- [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Vue d’ensemble de .NET pour les applications du Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
