---
title: <TimeSpan_LegacyFormatMode>, élément
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: 9d9eedf52f5d711412e4549e39e6ea23abb68ff3
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968905"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="ca32d-102">\<TimeSpan_LegacyFormatMode élément ></span><span class="sxs-lookup"><span data-stu-id="ca32d-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="ca32d-103">Détermine si le runtime conserve le comportement hérité dans les opérations de mise en forme avec des valeurs <xref:System.TimeSpan?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca32d-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

<span data-ttu-id="ca32d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca32d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ca32d-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca32d-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ca32d-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<** TimeSpan_LegacyFormatMode ></span><span class="sxs-lookup"><span data-stu-id="ca32d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="ca32d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca32d-107">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca32d-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ca32d-108">Attributes and Elements</span></span>

<span data-ttu-id="ca32d-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ca32d-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca32d-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="ca32d-110">Attributes</span></span>

|<span data-ttu-id="ca32d-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="ca32d-111">Attribute</span></span>|<span data-ttu-id="ca32d-112">Description</span><span class="sxs-lookup"><span data-stu-id="ca32d-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="ca32d-113">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="ca32d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ca32d-114">Spécifie si le runtime utilise le comportement de mise en forme hérité avec les valeurs de <xref:System.TimeSpan?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca32d-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="ca32d-115">Attribut enabled</span><span class="sxs-lookup"><span data-stu-id="ca32d-115">enabled Attribute</span></span>

|<span data-ttu-id="ca32d-116">valeur</span><span class="sxs-lookup"><span data-stu-id="ca32d-116">Value</span></span>|<span data-ttu-id="ca32d-117">Description</span><span class="sxs-lookup"><span data-stu-id="ca32d-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="ca32d-118">Le runtime ne restaure pas le comportement de mise en forme hérité.</span><span class="sxs-lookup"><span data-stu-id="ca32d-118">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="ca32d-119">Le runtime restaure le comportement de mise en forme hérité.</span><span class="sxs-lookup"><span data-stu-id="ca32d-119">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ca32d-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ca32d-120">Child Elements</span></span>

<span data-ttu-id="ca32d-121">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="ca32d-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ca32d-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ca32d-122">Parent Elements</span></span>

|<span data-ttu-id="ca32d-123">Élément</span><span class="sxs-lookup"><span data-stu-id="ca32d-123">Element</span></span>|<span data-ttu-id="ca32d-124">Description</span><span class="sxs-lookup"><span data-stu-id="ca32d-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ca32d-125">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca32d-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="ca32d-126">Contient des informations sur les options d'initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="ca32d-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ca32d-127">Notes</span><span class="sxs-lookup"><span data-stu-id="ca32d-127">Remarks</span></span>

<span data-ttu-id="ca32d-128">À partir du .NET Framework 4, la structure <xref:System.TimeSpan?displayProperty=nameWithType> implémente l’interface <xref:System.IFormattable> et prend en charge les opérations de mise en forme avec des chaînes de format standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="ca32d-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="ca32d-129">Si une méthode d’analyse rencontre un spécificateur de format ou une chaîne de format non prise en charge, elle lève une <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="ca32d-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="ca32d-130">Dans les versions précédentes de la .NET Framework, la structure de <xref:System.TimeSpan> n’a pas implémenté <xref:System.IFormattable> et ne prenait pas en charge les chaînes de format.</span><span class="sxs-lookup"><span data-stu-id="ca32d-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="ca32d-131">Toutefois, de nombreux développeurs supposaient par erreur que <xref:System.TimeSpan> prenait en charge un ensemble de chaînes de format et les utilisaient dans des [opérations de mise en forme composite](../../../../standard/base-types/composite-formatting.md) avec des méthodes telles que <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca32d-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ca32d-132">En règle générale, si un type implémente <xref:System.IFormattable> et prend en charge les chaînes de format, les appels aux méthodes de mise en forme avec des chaînes de format non prises en charge lèvent généralement une <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="ca32d-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="ca32d-133">Toutefois, étant donné que <xref:System.TimeSpan> n’a pas implémenté <xref:System.IFormattable>, le runtime a ignoré la chaîne de format et appelé à la place la méthode <xref:System.TimeSpan.ToString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca32d-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ca32d-134">Cela signifie que, bien que les chaînes de format n’aient aucun effet sur l’opération de mise en forme, leur présence n’a pas entraîné de <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="ca32d-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="ca32d-135">Dans les cas où le code hérité passe une méthode de mise en forme composite et une chaîne de format non valide, et que ce code ne peut pas être recompilé, vous pouvez utiliser l’élément `<TimeSpan_LegacyFormatMode>` pour restaurer le comportement <xref:System.TimeSpan> hérité.</span><span class="sxs-lookup"><span data-stu-id="ca32d-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="ca32d-136">Lorsque vous affectez à l’attribut `enabled` de cet élément la valeur `true`, la méthode de mise en forme composite entraîne un appel à <xref:System.TimeSpan.ToString?displayProperty=nameWithType> plutôt que <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, et une <xref:System.FormatException> n’est pas levée.</span><span class="sxs-lookup"><span data-stu-id="ca32d-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="ca32d-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="ca32d-137">Example</span></span>

<span data-ttu-id="ca32d-138">L’exemple suivant instancie un objet <xref:System.TimeSpan> et tente de le mettre en forme avec la méthode <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> à l’aide d’une chaîne de format standard non prise en charge.</span><span class="sxs-lookup"><span data-stu-id="ca32d-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="ca32d-139">Lorsque vous exécutez l’exemple sur la .NET Framework 3,5 ou sur une version antérieure, la sortie suivante s’affiche :</span><span class="sxs-lookup"><span data-stu-id="ca32d-139">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```console
12:30:45
```

<span data-ttu-id="ca32d-140">Cela diffère de façon marquée de la sortie si vous exécutez l’exemple sur le .NET Framework 4 ou version ultérieure :</span><span class="sxs-lookup"><span data-stu-id="ca32d-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```console
Invalid Format
```

<span data-ttu-id="ca32d-141">Toutefois, si vous ajoutez le fichier de configuration suivant au répertoire de l’exemple, puis exécutez l’exemple sur le .NET Framework 4 ou une version ultérieure, la sortie est identique à celle produite par l’exemple lorsqu’elle est exécutée sur .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="ca32d-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ca32d-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca32d-142">See also</span></span>

- [<span data-ttu-id="ca32d-143">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="ca32d-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ca32d-144">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="ca32d-144">Configuration File Schema</span></span>](../index.md)
