---
title: Marshaling par défaut pour les tableaux
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
ms.openlocfilehash: 8505f4c742fb002be249ab069708f7f768c672df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123576"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="08f99-102">Marshaling par défaut pour les tableaux</span><span class="sxs-lookup"><span data-stu-id="08f99-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="08f99-103">Dans une application composée dans son ensemble de code managé, le common language runtime passe des types tableau comme paramètres en entrée/sortie.</span><span class="sxs-lookup"><span data-stu-id="08f99-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="08f99-104">Par contre, le marshaleur d’interopérabilité passe un tableau comme paramètre en entrée par défaut.</span><span class="sxs-lookup"><span data-stu-id="08f99-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="08f99-105">Avec l’[optimisation de l’épinglage](copying-and-pinning.md), un tableau blittable peut sembler s’exécuter en tant que paramètre en entrée/sortie quand il interagit avec des objets dans le même cloisonnement.</span><span class="sxs-lookup"><span data-stu-id="08f99-105">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="08f99-106">Toutefois, si vous exportez ultérieurement le code dans une bibliothèque de types utilisée pour générer le proxy entre ordinateurs et que la bibliothèque est utilisée pour marshaler vos appels entre cloisonnements, les appels peuvent revenir à un vrai comportement de paramètre en entrée.</span><span class="sxs-lookup"><span data-stu-id="08f99-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="08f99-107">Les tableaux sont par nature complexes et les distinctions entre les tableaux managés et non managés justifient davantage d’informations que les autres types non blittables.</span><span class="sxs-lookup"><span data-stu-id="08f99-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="08f99-108">Tableaux managés</span><span class="sxs-lookup"><span data-stu-id="08f99-108">Managed Arrays</span></span>  
 <span data-ttu-id="08f99-109">Les types tableau managés sont divers ; cependant, la classe <xref:System.Array?displayProperty=nameWithType> est la classe de base de tous les types tableau.</span><span class="sxs-lookup"><span data-stu-id="08f99-109">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="08f99-110">La classe **System.Array** possède des propriétés permettant de déterminer le rang, la longueur et les limites inférieures et supérieures d’un tableau, ainsi que des méthodes permettant d’accéder, de trier, de rechercher, de copier et de créer des tableaux.</span><span class="sxs-lookup"><span data-stu-id="08f99-110">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="08f99-111">Ces types tableau sont dynamiques et n’ont pas de type statique correspondant défini dans la bibliothèque de classes de base.</span><span class="sxs-lookup"><span data-stu-id="08f99-111">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="08f99-112">Il est pratique de considérer chaque combinaison de type d’élément et de rang comme un type distinct de tableau.</span><span class="sxs-lookup"><span data-stu-id="08f99-112">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="08f99-113">Par conséquent, un tableau unidimensionnel d’entiers constitue un type différent par rapport à un tableau unidimensionnel de types doubles.</span><span class="sxs-lookup"><span data-stu-id="08f99-113">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="08f99-114">De même, un tableau à deux dimensions d’entiers constitue un type différent par rapport à un tableau unidimensionnel d’entiers.</span><span class="sxs-lookup"><span data-stu-id="08f99-114">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="08f99-115">Les limites du tableau ne sont pas prises en compte lors de la comparaison des types.</span><span class="sxs-lookup"><span data-stu-id="08f99-115">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="08f99-116">Comme le tableau ci-dessous l’indique, toute instance d’un tableau managé doit avoir un type d’élément, un rang et une limite inférieure spécifiques.</span><span class="sxs-lookup"><span data-stu-id="08f99-116">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="08f99-117">Type tableau managé</span><span class="sxs-lookup"><span data-stu-id="08f99-117">Managed array type</span></span>|<span data-ttu-id="08f99-118">Type d'élément</span><span class="sxs-lookup"><span data-stu-id="08f99-118">Element type</span></span>|<span data-ttu-id="08f99-119">Rang</span><span class="sxs-lookup"><span data-stu-id="08f99-119">Rank</span></span>|<span data-ttu-id="08f99-120">Limite inférieure</span><span class="sxs-lookup"><span data-stu-id="08f99-120">Lower bound</span></span>|<span data-ttu-id="08f99-121">Notation de signature</span><span class="sxs-lookup"><span data-stu-id="08f99-121">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="08f99-122">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="08f99-122">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="08f99-123">Spécifié par type.</span><span class="sxs-lookup"><span data-stu-id="08f99-123">Specified by type.</span></span>|<span data-ttu-id="08f99-124">Spécifié par rang.</span><span class="sxs-lookup"><span data-stu-id="08f99-124">Specified by rank.</span></span>|<span data-ttu-id="08f99-125">Spécifiée de manière facultative par des limites.</span><span class="sxs-lookup"><span data-stu-id="08f99-125">Optionally specified by bounds.</span></span>|<span data-ttu-id="08f99-126">*type* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="08f99-126">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="08f99-127">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="08f99-127">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="08f99-128">Inconnu</span><span class="sxs-lookup"><span data-stu-id="08f99-128">Unknown</span></span>|<span data-ttu-id="08f99-129">Inconnu</span><span class="sxs-lookup"><span data-stu-id="08f99-129">Unknown</span></span>|<span data-ttu-id="08f99-130">Inconnu</span><span class="sxs-lookup"><span data-stu-id="08f99-130">Unknown</span></span>|<span data-ttu-id="08f99-131">**System.Array**</span><span class="sxs-lookup"><span data-stu-id="08f99-131">**System.Array**</span></span>|  
|<span data-ttu-id="08f99-132">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="08f99-132">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="08f99-133">Spécifié par type.</span><span class="sxs-lookup"><span data-stu-id="08f99-133">Specified by type.</span></span>|<span data-ttu-id="08f99-134">1</span><span class="sxs-lookup"><span data-stu-id="08f99-134">1</span></span>|<span data-ttu-id="08f99-135">0</span><span class="sxs-lookup"><span data-stu-id="08f99-135">0</span></span>|<span data-ttu-id="08f99-136">*type* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="08f99-136">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="08f99-137">Tableaux non managés</span><span class="sxs-lookup"><span data-stu-id="08f99-137">Unmanaged Arrays</span></span>  
 <span data-ttu-id="08f99-138">Les tableaux non managés sont soit des tableaux sécurisés de style COM, soit des tableaux de style C de longueur fixe ou variable.</span><span class="sxs-lookup"><span data-stu-id="08f99-138">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="08f99-139">Les tableaux sécurisés sont des tableaux autodescriptifs qui comportent le type, le rang et les limites des données de tableau associées.</span><span class="sxs-lookup"><span data-stu-id="08f99-139">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="08f99-140">Les tableaux de style C sont des tableaux typés unidimensionnels dont la limite inférieure fixe est 0.</span><span class="sxs-lookup"><span data-stu-id="08f99-140">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="08f99-141">La prise en charge par le service marshaling de ces deux types de tableaux est limitée.</span><span class="sxs-lookup"><span data-stu-id="08f99-141">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="08f99-142">Passage de paramètres de tableau au code .NET</span><span class="sxs-lookup"><span data-stu-id="08f99-142">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="08f99-143">Les tableaux sécurisés et les tableaux de style C peuvent tous deux être passés à du code .NET à partir de code non managé soit comme tableau sécurisé, soit comme tableau de style C.</span><span class="sxs-lookup"><span data-stu-id="08f99-143">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="08f99-144">Le tableau suivant illustre la valeur de type non managé et le type importé.</span><span class="sxs-lookup"><span data-stu-id="08f99-144">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="08f99-145">Type non managé</span><span class="sxs-lookup"><span data-stu-id="08f99-145">Unmanaged type</span></span>|<span data-ttu-id="08f99-146">Type importé</span><span class="sxs-lookup"><span data-stu-id="08f99-146">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="08f99-147">**SafeArray(** *Type* **)**</span><span class="sxs-lookup"><span data-stu-id="08f99-147">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="08f99-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="08f99-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="08f99-149">Rang = 1, limite inférieure = 0.</span><span class="sxs-lookup"><span data-stu-id="08f99-149">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="08f99-150">La taille n’est connue que si elle est fournie dans la signature managée.</span><span class="sxs-lookup"><span data-stu-id="08f99-150">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="08f99-151">Les tableaux sécurisés qui n’ont pas le rang = 1 ou la limite inférieure = 0 ne peuvent pas être marshalés en tant que **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="08f99-151">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="08f99-152">*Type*  **[]**</span><span class="sxs-lookup"><span data-stu-id="08f99-152">*Type*  **[]**</span></span>|<span data-ttu-id="08f99-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="08f99-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="08f99-154">Rang = 1, limite inférieure = 0.</span><span class="sxs-lookup"><span data-stu-id="08f99-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="08f99-155">La taille n’est connue que si elle est fournie dans la signature managée.</span><span class="sxs-lookup"><span data-stu-id="08f99-155">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="08f99-156">Tableaux sécurisés</span><span class="sxs-lookup"><span data-stu-id="08f99-156">Safe Arrays</span></span>  
 <span data-ttu-id="08f99-157">Quand un tableau sécurisé est importé à partir d’une bibliothèque de types vers un assembly .NET, le tableau est converti en tableau unidimensionnel de type connu (comme **int**).</span><span class="sxs-lookup"><span data-stu-id="08f99-157">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="08f99-158">Les mêmes règles de conversion de type qui s’appliquent aux paramètres sont également valables pour les éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="08f99-158">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="08f99-159">Par exemple, un tableau sécurisé de types **BSTR** devient un tableau managé de chaînes et un tableau sécurisé de variants devient un tableau managé d’objets.</span><span class="sxs-lookup"><span data-stu-id="08f99-159">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="08f99-160">Le type d’élément **SAFEARRAY** est capturé à partir de la bibliothèque de types et enregistré dans la valeur **SAFEARRAY** de l’énumération <xref:System.Runtime.InteropServices.UnmanagedType>.</span><span class="sxs-lookup"><span data-stu-id="08f99-160">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="08f99-161">Étant donné que le rang et les limites du tableau sécurisé ne peuvent pas être déterminés à partir de la bibliothèque de types, le rang est considéré comme étant égal à 1 et la limite inférieure égale à 0.</span><span class="sxs-lookup"><span data-stu-id="08f99-161">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="08f99-162">Le rang et les limites doivent être définis dans la signature managée produite par l’outil [Tlbimp.exe (importateur de bibliothèques de types)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="08f99-162">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="08f99-163">Si le rang passé à la méthode au moment de l’exécution est différent, une exception <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> est levée.</span><span class="sxs-lookup"><span data-stu-id="08f99-163">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="08f99-164">Si le type du tableau passé au moment de l’exécution est différent, une exception <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> est levée.</span><span class="sxs-lookup"><span data-stu-id="08f99-164">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="08f99-165">L’exemple suivant montre des tableaux sécurisés dans du code managé et non managé.</span><span class="sxs-lookup"><span data-stu-id="08f99-165">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="08f99-166">**Signature non managée**</span><span class="sxs-lookup"><span data-stu-id="08f99-166">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="08f99-167">**Signature managée**</span><span class="sxs-lookup"><span data-stu-id="08f99-167">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _   
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _   
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]   
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]   
   ref String[] ar);  
```  
  
 <span data-ttu-id="08f99-168">Les tableaux sécurisés multidimensionnels ou non limités par zéro peuvent être marshalés dans du code managé si la signature de méthode produite par Tlbimp.exe est modifiée pour indiquer un type d’élément **ELEMENT_TYPE_ARRAY** au lieu d’**ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="08f99-168">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="08f99-169">Vous pouvez également utiliser le commutateur **/sysarray** avec Tlbimp.exe pour importer tous les tableaux en tant qu’objets <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="08f99-169">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="08f99-170">Pour les cas où le tableau passé se révèle être multidimensionnel, vous pouvez modifier le code MSIL (Microsoft Intermediate Language) produit par Tlimb.exe, puis le recompiler.</span><span class="sxs-lookup"><span data-stu-id="08f99-170">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="08f99-171">Pour plus d’informations sur la manière de modifier du code MSIL, consultez [Personnalisation des wrappers RCW](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="08f99-171">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="08f99-172">Tableaux de style C</span><span class="sxs-lookup"><span data-stu-id="08f99-172">C-Style Arrays</span></span>  
 <span data-ttu-id="08f99-173">Quand un tableau de style C est importé à partir d’une bibliothèque de types vers un assembly .NET, le tableau est converti en **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="08f99-173">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="08f99-174">Le type d’élément de tableau est déterminé à partir de la bibliothèque de types et préservé lors de l’importation.</span><span class="sxs-lookup"><span data-stu-id="08f99-174">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="08f99-175">Les mêmes règles de conversion qui s’appliquent aux paramètres sont également valables pour les éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="08f99-175">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="08f99-176">Par exemple, un tableau de types **LPStr** devient un tableau de types **String**.</span><span class="sxs-lookup"><span data-stu-id="08f99-176">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="08f99-177">Tlbimp.exe capture le type d’élément de tableau et applique l’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> au paramètre.</span><span class="sxs-lookup"><span data-stu-id="08f99-177">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="08f99-178">Le rang du tableau est considéré comme étant égal à 1.</span><span class="sxs-lookup"><span data-stu-id="08f99-178">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="08f99-179">Si le rang est supérieur à 1, le tableau est marshalé en tant que tableau unidimensionnel en colonne.</span><span class="sxs-lookup"><span data-stu-id="08f99-179">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="08f99-180">La limite inférieure est toujours égale à 0.</span><span class="sxs-lookup"><span data-stu-id="08f99-180">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="08f99-181">Des bibliothèques de types peuvent contenir des tableaux dont la longueur est fixe ou variable.</span><span class="sxs-lookup"><span data-stu-id="08f99-181">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="08f99-182">Tlbimp.exe peut importer uniquement des tableaux dont la longueur est fixe à partir des bibliothèques de types, car les bibliothèques de types ne disposent pas des informations nécessaires pour marshaler des tableaux de longueur variable.</span><span class="sxs-lookup"><span data-stu-id="08f99-182">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="08f99-183">Pour les tableaux de longueur fixe, la taille est importée à partir de la bibliothèque de types et capturée dans le **MarshalAsAttribute** qui est appliqué au paramètre.</span><span class="sxs-lookup"><span data-stu-id="08f99-183">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="08f99-184">Vous devez définir manuellement les bibliothèques de types contenant des tableaux de longueur variable comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="08f99-184">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="08f99-185">**Signature non managée**</span><span class="sxs-lookup"><span data-stu-id="08f99-185">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="08f99-186">**Signature managée**</span><span class="sxs-lookup"><span data-stu-id="08f99-186">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,   
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 <span data-ttu-id="08f99-187">Bien qu’il vous soit possible d’appliquer les attributs **size_is** ou **length_is** à un tableau dans la source IDL (Interface Definition Language) pour décrire la taille au client, le compilateur MIDL (Microsoft Interface Definition Language) ne propage pas ces informations à la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="08f99-187">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="08f99-188">Sans connaissance de la taille, le service marshaling d’interopérabilité ne peut pas marshaler les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="08f99-188">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="08f99-189">Par conséquent, les tableaux de longueur variable sont importés comme arguments de référence.</span><span class="sxs-lookup"><span data-stu-id="08f99-189">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="08f99-190">Exemple :</span><span class="sxs-lookup"><span data-stu-id="08f99-190">For example:</span></span>  
  
 <span data-ttu-id="08f99-191">**Signature non managée**</span><span class="sxs-lookup"><span data-stu-id="08f99-191">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="08f99-192">**Signature managée**</span><span class="sxs-lookup"><span data-stu-id="08f99-192">**Managed signature**</span></span>  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
```  
  
```csharp  
void New1(ref int ar);    
void New2(ref double ar);    
void New3(ref String ar);   
```  
  
 <span data-ttu-id="08f99-193">Vous pouvez fournir la taille du tableau au marshaleur en éditant le code MSIL produit par Tlbimp.exe, puis en le recompilant.</span><span class="sxs-lookup"><span data-stu-id="08f99-193">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="08f99-194">Pour plus d’informations sur la manière de modifier du code MSIL, consultez [Personnalisation des wrappers RCW](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="08f99-194">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="08f99-195">Pour indiquer le nombre d’éléments figurant dans le tableau, appliquez le type <xref:System.Runtime.InteropServices.MarshalAsAttribute> au paramètre de tableau de la définition de méthode managée en procédant de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="08f99-195">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
- <span data-ttu-id="08f99-196">Identifiez un autre paramètre qui contient le nombre d’éléments figurant dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="08f99-196">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="08f99-197">Les paramètres sont identifiés par position, le premier portant le numéro 0.</span><span class="sxs-lookup"><span data-stu-id="08f99-197">The parameters are identified by position, starting with the first parameter as number 0.</span></span>     
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       \<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,   
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
- <span data-ttu-id="08f99-198">Définissez la taille du tableau comme constante.</span><span class="sxs-lookup"><span data-stu-id="08f99-198">Define the size of the array as a constant.</span></span> <span data-ttu-id="08f99-199">Exemple :</span><span class="sxs-lookup"><span data-stu-id="08f99-199">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="08f99-200">Quand il marshale des tableaux à partir du code non managé vers le code managé, le marshaleur vérifie l’attribut **MarshalAsAttribute** associé au paramètre pour déterminer la taille du tableau.</span><span class="sxs-lookup"><span data-stu-id="08f99-200">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="08f99-201">Si la taille du tableau n’est pas spécifiée, seul un élément est marshalé.</span><span class="sxs-lookup"><span data-stu-id="08f99-201">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08f99-202">L’attribut **MarshalAsAttribute** n’a aucun effet sur le marshaling de tableaux managés vers du code non managé.</span><span class="sxs-lookup"><span data-stu-id="08f99-202">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="08f99-203">Dans ce sens, la taille du tableau est déterminée par examen.</span><span class="sxs-lookup"><span data-stu-id="08f99-203">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="08f99-204">Il est impossible de marshaler un sous-ensemble d’un tableau managé.</span><span class="sxs-lookup"><span data-stu-id="08f99-204">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="08f99-205">Le marshaleur d’interopérabilité utilise les méthodes **CoTaskMemAlloc** et **CoTaskMemFree** pour allouer et récupérer de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="08f99-205">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="08f99-206">L’allocation de mémoire effectuée par le code non managé doit également utiliser ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="08f99-206">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="08f99-207">Passage de tableaux à COM</span><span class="sxs-lookup"><span data-stu-id="08f99-207">Passing Arrays to COM</span></span>  
 <span data-ttu-id="08f99-208">Tous les types tableau managés peuvent être passés au code non managé à partir du code managé.</span><span class="sxs-lookup"><span data-stu-id="08f99-208">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="08f99-209">En fonction du type managé et des attributs qui lui sont appliqués, le tableau est accessible comme tableau sécurisé ou comme tableau de style C, comme le montre le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="08f99-209">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="08f99-210">Type tableau managé</span><span class="sxs-lookup"><span data-stu-id="08f99-210">Managed array type</span></span>|<span data-ttu-id="08f99-211">Exporté comme</span><span class="sxs-lookup"><span data-stu-id="08f99-211">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="08f99-212">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span><span class="sxs-lookup"><span data-stu-id="08f99-212">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="08f99-213"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="08f99-213"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="08f99-214">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="08f99-214">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="08f99-215">Type est fourni dans la signature.</span><span class="sxs-lookup"><span data-stu-id="08f99-215">Type is provided in the signature.</span></span> <span data-ttu-id="08f99-216">Le rang est toujours 1, la limite inférieure est toujours 0.</span><span class="sxs-lookup"><span data-stu-id="08f99-216">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="08f99-217">La taille est toujours connue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="08f99-217">Size is always known at run time.</span></span>|  
|<span data-ttu-id="08f99-218">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rang* **>** [ **\<** *limites* **>** ]</span><span class="sxs-lookup"><span data-stu-id="08f99-218">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="08f99-219">**UnmanagedType.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="08f99-219">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="08f99-220">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="08f99-220">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="08f99-221">Type, rang et limites sont fournis dans la signature.</span><span class="sxs-lookup"><span data-stu-id="08f99-221">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="08f99-222">La taille est toujours connue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="08f99-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="08f99-223">**ELEMENT_TYPE_CLASS** **\<** <xref:System.Array?displayProperty=nameWithType> **>**</span><span class="sxs-lookup"><span data-stu-id="08f99-223">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span></span>|<span data-ttu-id="08f99-224">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="08f99-224">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="08f99-225">**UnmanagedType.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="08f99-225">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="08f99-226">Type, rang, limites et taille sont toujours connus au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="08f99-226">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="08f99-227">Il existe une restriction dans OLE Automation concernant les tableaux de structures qui contiennent LPSTR ou LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="08f99-227">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="08f99-228">Par conséquent, les champs **String** doivent être marshalés comme **UnmanagedType.BSTR**.</span><span class="sxs-lookup"><span data-stu-id="08f99-228">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="08f99-229">Sinon, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="08f99-229">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="element_type_szarray"></a><span data-ttu-id="08f99-230">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="08f99-230">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="08f99-231">Quand une méthode contenant un paramètre **ELEMENT_TYPE_SZARRAY** (tableau unidimensionnel) est exportée à partir d’un assembly .NET vers une bibliothèque de types, le paramètre de tableau est converti en un **SAFEARRAY** d’un type donné.</span><span class="sxs-lookup"><span data-stu-id="08f99-231">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="08f99-232">Les mêmes règles de conversion s’appliquent aux types d’éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="08f99-232">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="08f99-233">Le contenu du tableau managé est automatiquement copié à partir de la mémoire managée dans le **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="08f99-233">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="08f99-234">Exemple :</span><span class="sxs-lookup"><span data-stu-id="08f99-234">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="08f99-235">Signature managée</span><span class="sxs-lookup"><span data-stu-id="08f99-235">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="08f99-236">Signature non managée</span><span class="sxs-lookup"><span data-stu-id="08f99-236">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="08f99-237">Le rang des tableaux sécurisés est toujours 1 et la limite inférieure est toujours 0.</span><span class="sxs-lookup"><span data-stu-id="08f99-237">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="08f99-238">La taille est déterminée au moment de l’exécution par la taille du tableau managé qui est passé.</span><span class="sxs-lookup"><span data-stu-id="08f99-238">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="08f99-239">Le tableau peut également être marshalé en tant que tableau de style C en utilisant l’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="08f99-239">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="08f99-240">Exemple :</span><span class="sxs-lookup"><span data-stu-id="08f99-240">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="08f99-241">Signature managée</span><span class="sxs-lookup"><span data-stu-id="08f99-241">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]   
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=   
   UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="08f99-242">Signature non managée</span><span class="sxs-lookup"><span data-stu-id="08f99-242">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="08f99-243">Bien que le marshaleur possède les informations de longueur nécessaires pour marshaler le tableau, la longueur du tableau est généralement passée comme argument séparé afin de l’envoyer à l’appelé.</span><span class="sxs-lookup"><span data-stu-id="08f99-243">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="element_type_array"></a><span data-ttu-id="08f99-244">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="08f99-244">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="08f99-245">Quand une méthode contenant un paramètre **ELEMENT_TYPE_ARRAY** est exportée à partir d’un assembly .NET vers une bibliothèque de types, le paramètre de tableau est converti en un **SAFEARRAY** d’un type donné.</span><span class="sxs-lookup"><span data-stu-id="08f99-245">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="08f99-246">Le contenu du tableau managé est automatiquement copié à partir de la mémoire managée dans le **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="08f99-246">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="08f99-247">Exemple :</span><span class="sxs-lookup"><span data-stu-id="08f99-247">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="08f99-248">Signature managée</span><span class="sxs-lookup"><span data-stu-id="08f99-248">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="08f99-249">Signature non managée</span><span class="sxs-lookup"><span data-stu-id="08f99-249">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="08f99-250">Le rang, la taille et les limites des tableaux sécurisés sont déterminés au moment de l’exécution par les caractéristiques du tableau managé.</span><span class="sxs-lookup"><span data-stu-id="08f99-250">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="08f99-251">Le tableau peut également être marshalé en tant que tableau de style C en appliquant l’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="08f99-251">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="08f99-252">Exemple :</span><span class="sxs-lookup"><span data-stu-id="08f99-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="08f99-253">Signature managée</span><span class="sxs-lookup"><span data-stu-id="08f99-253">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]   
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,   
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]   
   String [,] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="08f99-254">Signature non managée</span><span class="sxs-lookup"><span data-stu-id="08f99-254">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="08f99-255">Les tableaux imbriqués ne peuvent pas être marshalés.</span><span class="sxs-lookup"><span data-stu-id="08f99-255">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="08f99-256">Par exemple, la signature suivante génère une erreur quand elle est exportée à l’aide de l’outil [Tlbexp.exe (exportateur de bibliothèques de types)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="08f99-256">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="08f99-257">Signature managée</span><span class="sxs-lookup"><span data-stu-id="08f99-257">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a><span data-ttu-id="08f99-258">ELEMENT_TYPE_CLASS \<System.Array></span><span class="sxs-lookup"><span data-stu-id="08f99-258">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="08f99-259">Quand une méthode contenant un paramètre <xref:System.Array?displayProperty=nameWithType> est exportée à partir d’un assembly .NET vers une bibliothèque de types, le paramètre de tableau est converti en une interface **_Array**.</span><span class="sxs-lookup"><span data-stu-id="08f99-259">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="08f99-260">Le contenu du tableau managé est accessible uniquement par les méthodes et les propriétés de l’interface **_Array**.</span><span class="sxs-lookup"><span data-stu-id="08f99-260">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="08f99-261">La méthode **System.Array** peut également être marshalée comme un **SAFEARRAY** à l’aide de l’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="08f99-261">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="08f99-262">Quand ils sont marshalés comme tableau sécurisé, les éléments du tableau sont marshalés comme variants.</span><span class="sxs-lookup"><span data-stu-id="08f99-262">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="08f99-263">Exemple :</span><span class="sxs-lookup"><span data-stu-id="08f99-263">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="08f99-264">Signature managée</span><span class="sxs-lookup"><span data-stu-id="08f99-264">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="08f99-265">Signature non managée</span><span class="sxs-lookup"><span data-stu-id="08f99-265">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="08f99-266">Tableaux à l’intérieur de structures</span><span class="sxs-lookup"><span data-stu-id="08f99-266">Arrays within Structures</span></span>  
 <span data-ttu-id="08f99-267">Les structures non managées peuvent contenir des tableaux incorporés.</span><span class="sxs-lookup"><span data-stu-id="08f99-267">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="08f99-268">Par défaut, ces champs de tableau incorporés sont marshalés en tant que SAFEARRAY.</span><span class="sxs-lookup"><span data-stu-id="08f99-268">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="08f99-269">Dans l’exemple suivant, `s1` est un tableau incorporé qui est alloué directement au sein de la structure elle-même.</span><span class="sxs-lookup"><span data-stu-id="08f99-269">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="08f99-270">Représentation non managée</span><span class="sxs-lookup"><span data-stu-id="08f99-270">Unmanaged representation</span></span>  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="08f99-271">Les tableaux peuvent être marshalés comme <xref:System.Runtime.InteropServices.UnmanagedType>, ce qui exige que vous définissiez le champ <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="08f99-271">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="08f99-272">La taille peut être définie uniquement comme constante.</span><span class="sxs-lookup"><span data-stu-id="08f99-272">The size can be set only as a constant.</span></span> <span data-ttu-id="08f99-273">Le code suivant montre la définition managée correspondante de `MyStruct`.</span><span class="sxs-lookup"><span data-stu-id="08f99-273">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="08f99-274">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08f99-274">See also</span></span>

- [<span data-ttu-id="08f99-275">Comportement de marshaling par défaut</span><span class="sxs-lookup"><span data-stu-id="08f99-275">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="08f99-276">Types blittable et non blittable</span><span class="sxs-lookup"><span data-stu-id="08f99-276">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="08f99-277">[Attributs directionnels](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="08f99-277">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="08f99-278">Copie et épinglage</span><span class="sxs-lookup"><span data-stu-id="08f99-278">Copying and Pinning</span></span>](copying-and-pinning.md)
