---
title: Collections de schémas OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 90899a123b3dafcd47a50ef8f6eb003938b22a03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186937"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="0da0b-102">Collections de schémas OLE DB</span><span class="sxs-lookup"><span data-stu-id="0da0b-102">OLE DB Schema Collections</span></span>

<span data-ttu-id="0da0b-103">Cette section traite de la prise en charge des collections de schémas pour les fournisseurs OLE DB de Microsoft SQL Server, Oracle et Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="0da0b-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="0da0b-104">Fournisseur Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="0da0b-104">Microsoft SQL Server OLE DB Provider</span></span>  

 <span data-ttu-id="0da0b-105">Le pilote Microsoft SQL Server OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="0da0b-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="0da0b-106">Tables</span><span class="sxs-lookup"><span data-stu-id="0da0b-106">Tables</span></span>  
  
- <span data-ttu-id="0da0b-107">Colonnes</span><span class="sxs-lookup"><span data-stu-id="0da0b-107">Columns</span></span>  
  
- <span data-ttu-id="0da0b-108">Procédures</span><span class="sxs-lookup"><span data-stu-id="0da0b-108">Procedures</span></span>  
  
- <span data-ttu-id="0da0b-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0da0b-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="0da0b-110">Catalogue</span><span class="sxs-lookup"><span data-stu-id="0da0b-110">Catalog</span></span>  
  
- <span data-ttu-id="0da0b-111">Index</span><span class="sxs-lookup"><span data-stu-id="0da0b-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0da0b-112">Tables</span><span class="sxs-lookup"><span data-stu-id="0da0b-112">Tables</span></span>  
  
|<span data-ttu-id="0da0b-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-113">ColumnName</span></span>|<span data-ttu-id="0da0b-114">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-115">TABLE_CATALOG</span></span>|<span data-ttu-id="0da0b-116">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-116">String</span></span>|  
|<span data-ttu-id="0da0b-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="0da0b-118">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-118">String</span></span>|  
|<span data-ttu-id="0da0b-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-119">TABLE_NAME</span></span>|<span data-ttu-id="0da0b-120">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-120">String</span></span>|  
|<span data-ttu-id="0da0b-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-121">TABLE_TYPE</span></span>|<span data-ttu-id="0da0b-122">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-122">String</span></span>|  
|<span data-ttu-id="0da0b-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-123">TABLE_GUID</span></span>|<span data-ttu-id="0da0b-124">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-124">Guid</span></span>|  
|<span data-ttu-id="0da0b-125">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-125">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-126">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-126">String</span></span>|  
|<span data-ttu-id="0da0b-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0da0b-127">TABLE_PROPID</span></span>|<span data-ttu-id="0da0b-128">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-128">Int64</span></span>|  
|<span data-ttu-id="0da0b-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0da0b-129">DATE_CREATED</span></span>|<span data-ttu-id="0da0b-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-130">DateTime</span></span>|  
|<span data-ttu-id="0da0b-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0da0b-131">DATE_MODIFIED</span></span>|<span data-ttu-id="0da0b-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0da0b-133">Colonnes</span><span class="sxs-lookup"><span data-stu-id="0da0b-133">Columns</span></span>  
  
|<span data-ttu-id="0da0b-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-134">ColumnName</span></span>|<span data-ttu-id="0da0b-135">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-136">TABLE_CATALOG</span></span>|<span data-ttu-id="0da0b-137">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-137">String</span></span>|  
|<span data-ttu-id="0da0b-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="0da0b-139">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-139">String</span></span>|  
|<span data-ttu-id="0da0b-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-140">TABLE_NAME</span></span>|<span data-ttu-id="0da0b-141">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-141">String</span></span>|  
|<span data-ttu-id="0da0b-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-142">COLUMN_NAME</span></span>|<span data-ttu-id="0da0b-143">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-143">String</span></span>|  
|<span data-ttu-id="0da0b-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-144">COLUMN_GUID</span></span>|<span data-ttu-id="0da0b-145">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-145">Guid</span></span>|  
|<span data-ttu-id="0da0b-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0da0b-146">COLUMN_PROPID</span></span>|<span data-ttu-id="0da0b-147">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-147">Int64</span></span>|  
|<span data-ttu-id="0da0b-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="0da0b-149">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-149">Int64</span></span>|  
|<span data-ttu-id="0da0b-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0da0b-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0da0b-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-151">Boolean</span></span>|  
|<span data-ttu-id="0da0b-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0da0b-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0da0b-153">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-153">String</span></span>|  
|<span data-ttu-id="0da0b-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0da0b-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="0da0b-155">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-155">Int64</span></span>|  
|<span data-ttu-id="0da0b-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0da0b-156">IS_NULLABLE</span></span>|<span data-ttu-id="0da0b-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-157">Boolean</span></span>|  
|<span data-ttu-id="0da0b-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-158">DATA_TYPE</span></span>|<span data-ttu-id="0da0b-159">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-159">Int32</span></span>|  
|<span data-ttu-id="0da0b-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-160">TYPE_GUID</span></span>|<span data-ttu-id="0da0b-161">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-161">Guid</span></span>|  
|<span data-ttu-id="0da0b-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0da0b-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0da0b-163">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-163">Int64</span></span>|  
|<span data-ttu-id="0da0b-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0da0b-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0da0b-165">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-165">Int64</span></span>|  
|<span data-ttu-id="0da0b-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0da0b-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0da0b-167">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-167">Int32</span></span>|  
|<span data-ttu-id="0da0b-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0da0b-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="0da0b-169">Int16</span><span class="sxs-lookup"><span data-stu-id="0da0b-169">Int16</span></span>|  
|<span data-ttu-id="0da0b-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0da0b-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="0da0b-171">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-171">Int64</span></span>|  
|<span data-ttu-id="0da0b-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0da0b-173">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-173">String</span></span>|  
|<span data-ttu-id="0da0b-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0da0b-175">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-175">String</span></span>|  
|<span data-ttu-id="0da0b-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0da0b-177">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-177">String</span></span>|  
|<span data-ttu-id="0da0b-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="0da0b-179">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-179">String</span></span>|  
|<span data-ttu-id="0da0b-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0da0b-181">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-181">String</span></span>|  
|<span data-ttu-id="0da0b-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-182">COLLATION_NAME</span></span>|<span data-ttu-id="0da0b-183">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-183">String</span></span>|  
|<span data-ttu-id="0da0b-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0da0b-185">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-185">String</span></span>|  
|<span data-ttu-id="0da0b-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0da0b-187">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-187">String</span></span>|  
|<span data-ttu-id="0da0b-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-188">DOMAIN_NAME</span></span>|<span data-ttu-id="0da0b-189">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-189">String</span></span>|  
|<span data-ttu-id="0da0b-190">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-190">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-191">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-191">String</span></span>|  
|<span data-ttu-id="0da0b-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="0da0b-192">COLUMN_LCID</span></span>|<span data-ttu-id="0da0b-193">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-193">Int32</span></span>|  
|<span data-ttu-id="0da0b-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="0da0b-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="0da0b-195">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-195">Int32</span></span>|  
|<span data-ttu-id="0da0b-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="0da0b-196">COLUMN_SORTID</span></span>|<span data-ttu-id="0da0b-197">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-197">Int32</span></span>|  
|<span data-ttu-id="0da0b-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="0da0b-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="0da0b-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="0da0b-199">Byte[]</span></span>|  
|<span data-ttu-id="0da0b-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="0da0b-200">IS_COMPUTED</span></span>|<span data-ttu-id="0da0b-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0da0b-202">Procédures</span><span class="sxs-lookup"><span data-stu-id="0da0b-202">Procedures</span></span>  
  
|<span data-ttu-id="0da0b-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-203">ColumnName</span></span>|<span data-ttu-id="0da0b-204">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0da0b-206">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-206">String</span></span>|  
|<span data-ttu-id="0da0b-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0da0b-208">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-208">String</span></span>|  
|<span data-ttu-id="0da0b-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="0da0b-210">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-210">String</span></span>|  
|<span data-ttu-id="0da0b-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0da0b-212">Int16</span><span class="sxs-lookup"><span data-stu-id="0da0b-212">Int16</span></span>|  
|<span data-ttu-id="0da0b-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0da0b-214">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-214">String</span></span>|  
|<span data-ttu-id="0da0b-215">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-215">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-216">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-216">String</span></span>|  
|<span data-ttu-id="0da0b-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0da0b-217">DATE_CREATED</span></span>|<span data-ttu-id="0da0b-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-218">DateTime</span></span>|  
|<span data-ttu-id="0da0b-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0da0b-219">DATE_MODIFIED</span></span>|<span data-ttu-id="0da0b-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="0da0b-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0da0b-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="0da0b-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-222">ColumnName</span></span>|<span data-ttu-id="0da0b-223">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0da0b-225">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-225">String</span></span>|  
|<span data-ttu-id="0da0b-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0da0b-227">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-227">String</span></span>|  
|<span data-ttu-id="0da0b-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="0da0b-229">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-229">String</span></span>|  
|<span data-ttu-id="0da0b-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-230">PARAMETER_NAME</span></span>|<span data-ttu-id="0da0b-231">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-231">String</span></span>|  
|<span data-ttu-id="0da0b-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="0da0b-233">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-233">Int32</span></span>|  
|<span data-ttu-id="0da0b-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="0da0b-235">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-235">Int32</span></span>|  
|<span data-ttu-id="0da0b-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0da0b-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="0da0b-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-237">Boolean</span></span>|  
|<span data-ttu-id="0da0b-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0da0b-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="0da0b-239">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-239">String</span></span>|  
|<span data-ttu-id="0da0b-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0da0b-240">IS_NULLABLE</span></span>|<span data-ttu-id="0da0b-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-241">Boolean</span></span>|  
|<span data-ttu-id="0da0b-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-242">DATA_TYPE</span></span>|<span data-ttu-id="0da0b-243">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-243">Int32</span></span>|  
|<span data-ttu-id="0da0b-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0da0b-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0da0b-245">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-245">Int64</span></span>|  
|<span data-ttu-id="0da0b-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0da0b-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0da0b-247">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-247">Int64</span></span>|  
|<span data-ttu-id="0da0b-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0da0b-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0da0b-249">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-249">Int32</span></span>|  
|<span data-ttu-id="0da0b-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0da0b-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="0da0b-251">Int16</span><span class="sxs-lookup"><span data-stu-id="0da0b-251">Int16</span></span>|  
|<span data-ttu-id="0da0b-252">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-252">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-253">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-253">String</span></span>|  
|<span data-ttu-id="0da0b-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-254">TYPE_NAME</span></span>|<span data-ttu-id="0da0b-255">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-255">String</span></span>|  
|<span data-ttu-id="0da0b-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="0da0b-257">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="0da0b-258">Catalogue</span><span class="sxs-lookup"><span data-stu-id="0da0b-258">Catalog</span></span>  
  
|<span data-ttu-id="0da0b-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-259">ColumnName</span></span>|<span data-ttu-id="0da0b-260">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-261">CATALOG_NAME</span></span>|<span data-ttu-id="0da0b-262">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-262">String</span></span>|  
|<span data-ttu-id="0da0b-263">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-263">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-264">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0da0b-265">Index</span><span class="sxs-lookup"><span data-stu-id="0da0b-265">Indexes</span></span>  
  
|<span data-ttu-id="0da0b-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-266">ColumnName</span></span>|<span data-ttu-id="0da0b-267">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-268">TABLE_CATALOG</span></span>|<span data-ttu-id="0da0b-269">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-269">String</span></span>|  
|<span data-ttu-id="0da0b-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="0da0b-271">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-271">String</span></span>|  
|<span data-ttu-id="0da0b-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-272">TABLE_NAME</span></span>|<span data-ttu-id="0da0b-273">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-273">String</span></span>|  
|<span data-ttu-id="0da0b-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-274">INDEX_CATALOG</span></span>|<span data-ttu-id="0da0b-275">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-275">String</span></span>|  
|<span data-ttu-id="0da0b-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="0da0b-277">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-277">String</span></span>|  
|<span data-ttu-id="0da0b-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-278">INDEX_NAME</span></span>|<span data-ttu-id="0da0b-279">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-279">String</span></span>|  
|<span data-ttu-id="0da0b-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0da0b-280">PRIMARY_KEY</span></span>|<span data-ttu-id="0da0b-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-281">Boolean</span></span>|  
|<span data-ttu-id="0da0b-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0da0b-282">UNIQUE</span></span>|<span data-ttu-id="0da0b-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-283">Boolean</span></span>|  
|<span data-ttu-id="0da0b-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0da0b-284">CLUSTERED</span></span>|<span data-ttu-id="0da0b-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-285">Boolean</span></span>|  
|<span data-ttu-id="0da0b-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-286">TYPE</span></span>|<span data-ttu-id="0da0b-287">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-287">Int32</span></span>|  
|<span data-ttu-id="0da0b-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0da0b-288">FILL_FACTOR</span></span>|<span data-ttu-id="0da0b-289">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-289">Int32</span></span>|  
|<span data-ttu-id="0da0b-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0da0b-290">INITIAL_SIZE</span></span>|<span data-ttu-id="0da0b-291">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-291">Int32</span></span>|  
|<span data-ttu-id="0da0b-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="0da0b-292">NULLS</span></span>|<span data-ttu-id="0da0b-293">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-293">Int32</span></span>|  
|<span data-ttu-id="0da0b-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0da0b-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0da0b-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-295">Boolean</span></span>|  
|<span data-ttu-id="0da0b-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0da0b-296">AUTO_UPDATE</span></span>|<span data-ttu-id="0da0b-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-297">Boolean</span></span>|  
|<span data-ttu-id="0da0b-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0da0b-298">NULL_COLLATION</span></span>|<span data-ttu-id="0da0b-299">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-299">Int32</span></span>|  
|<span data-ttu-id="0da0b-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="0da0b-301">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-301">Int64</span></span>|  
|<span data-ttu-id="0da0b-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-302">COLUMN_NAME</span></span>|<span data-ttu-id="0da0b-303">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-303">String</span></span>|  
|<span data-ttu-id="0da0b-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-304">COLUMN_GUID</span></span>|<span data-ttu-id="0da0b-305">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-305">Guid</span></span>|  
|<span data-ttu-id="0da0b-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0da0b-306">COLUMN_PROPID</span></span>|<span data-ttu-id="0da0b-307">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-307">Int64</span></span>|  
|<span data-ttu-id="0da0b-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="0da0b-308">COLLATION</span></span>|<span data-ttu-id="0da0b-309">Int16</span><span class="sxs-lookup"><span data-stu-id="0da0b-309">Int16</span></span>|  
|<span data-ttu-id="0da0b-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="0da0b-310">CARDINALITY</span></span>|<span data-ttu-id="0da0b-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="0da0b-311">Decimal</span></span>|  
|<span data-ttu-id="0da0b-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="0da0b-312">PAGES</span></span>|<span data-ttu-id="0da0b-313">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-313">Int32</span></span>|  
|<span data-ttu-id="0da0b-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-314">FILTER_CONDITION</span></span>|<span data-ttu-id="0da0b-315">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-315">String</span></span>|  
|<span data-ttu-id="0da0b-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="0da0b-316">INTEGRATED</span></span>|<span data-ttu-id="0da0b-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="0da0b-318">Fournisseur Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="0da0b-318">Microsoft Oracle OLE DB Provider</span></span>  

 <span data-ttu-id="0da0b-319">Le pilote Microsoft Oracle OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="0da0b-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="0da0b-320">Tables</span><span class="sxs-lookup"><span data-stu-id="0da0b-320">Tables</span></span>  
  
- <span data-ttu-id="0da0b-321">Colonnes</span><span class="sxs-lookup"><span data-stu-id="0da0b-321">Columns</span></span>  
  
- <span data-ttu-id="0da0b-322">Procédures</span><span class="sxs-lookup"><span data-stu-id="0da0b-322">Procedures</span></span>  
  
- <span data-ttu-id="0da0b-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0da0b-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="0da0b-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="0da0b-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="0da0b-325">Les vues</span><span class="sxs-lookup"><span data-stu-id="0da0b-325">Views</span></span>  
  
- <span data-ttu-id="0da0b-326">Index</span><span class="sxs-lookup"><span data-stu-id="0da0b-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0da0b-327">Tables</span><span class="sxs-lookup"><span data-stu-id="0da0b-327">Tables</span></span>  
  
|<span data-ttu-id="0da0b-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-328">ColumnName</span></span>|<span data-ttu-id="0da0b-329">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-330">TABLE_CATALOG</span></span>|<span data-ttu-id="0da0b-331">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-331">String</span></span>|  
|<span data-ttu-id="0da0b-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="0da0b-333">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-333">String</span></span>|  
|<span data-ttu-id="0da0b-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-334">TABLE_NAME</span></span>|<span data-ttu-id="0da0b-335">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-335">String</span></span>|  
|<span data-ttu-id="0da0b-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-336">TABLE_TYPE</span></span>|<span data-ttu-id="0da0b-337">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-337">String</span></span>|  
|<span data-ttu-id="0da0b-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-338">TABLE_GUID</span></span>|<span data-ttu-id="0da0b-339">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-339">Guid</span></span>|  
|<span data-ttu-id="0da0b-340">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-340">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-341">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-341">String</span></span>|  
|<span data-ttu-id="0da0b-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0da0b-342">TABLE_PROPID</span></span>|<span data-ttu-id="0da0b-343">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-343">Int64</span></span>|  
|<span data-ttu-id="0da0b-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0da0b-344">DATE_CREATED</span></span>|<span data-ttu-id="0da0b-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-345">DateTime</span></span>|  
|<span data-ttu-id="0da0b-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0da0b-346">DATE_MODIFIED</span></span>|<span data-ttu-id="0da0b-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0da0b-348">Colonnes</span><span class="sxs-lookup"><span data-stu-id="0da0b-348">Columns</span></span>  
  
|<span data-ttu-id="0da0b-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-349">ColumnName</span></span>|<span data-ttu-id="0da0b-350">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-351">TABLE_CATALOG</span></span>|<span data-ttu-id="0da0b-352">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-352">String</span></span>|  
|<span data-ttu-id="0da0b-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="0da0b-354">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-354">String</span></span>|  
|<span data-ttu-id="0da0b-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-355">TABLE_NAME</span></span>|<span data-ttu-id="0da0b-356">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-356">String</span></span>|  
|<span data-ttu-id="0da0b-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-357">COLUMN_NAME</span></span>|<span data-ttu-id="0da0b-358">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-358">String</span></span>|  
|<span data-ttu-id="0da0b-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-359">COLUMN_GUID</span></span>|<span data-ttu-id="0da0b-360">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-360">Guid</span></span>|  
|<span data-ttu-id="0da0b-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0da0b-361">COLUMN_PROPID</span></span>|<span data-ttu-id="0da0b-362">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-362">Int64</span></span>|  
|<span data-ttu-id="0da0b-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="0da0b-364">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-364">Int64</span></span>|  
|<span data-ttu-id="0da0b-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0da0b-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0da0b-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-366">Boolean</span></span>|  
|<span data-ttu-id="0da0b-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0da0b-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0da0b-368">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-368">String</span></span>|  
|<span data-ttu-id="0da0b-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0da0b-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="0da0b-370">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-370">Int64</span></span>|  
|<span data-ttu-id="0da0b-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0da0b-371">IS_NULLABLE</span></span>|<span data-ttu-id="0da0b-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-372">Boolean</span></span>|  
|<span data-ttu-id="0da0b-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-373">DATA_TYPE</span></span>|<span data-ttu-id="0da0b-374">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-374">Int32</span></span>|  
|<span data-ttu-id="0da0b-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-375">TYPE_GUID</span></span>|<span data-ttu-id="0da0b-376">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-376">Guid</span></span>|  
|<span data-ttu-id="0da0b-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0da0b-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0da0b-378">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-378">Int64</span></span>|  
|<span data-ttu-id="0da0b-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0da0b-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0da0b-380">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-380">Int64</span></span>|  
|<span data-ttu-id="0da0b-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0da0b-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0da0b-382">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-382">Int32</span></span>|  
|<span data-ttu-id="0da0b-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0da0b-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="0da0b-384">Int16</span><span class="sxs-lookup"><span data-stu-id="0da0b-384">Int16</span></span>|  
|<span data-ttu-id="0da0b-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0da0b-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="0da0b-386">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-386">Int64</span></span>|  
|<span data-ttu-id="0da0b-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0da0b-388">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-388">String</span></span>|  
|<span data-ttu-id="0da0b-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0da0b-390">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-390">String</span></span>|  
|<span data-ttu-id="0da0b-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0da0b-392">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-392">String</span></span>|  
|<span data-ttu-id="0da0b-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="0da0b-394">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-394">String</span></span>|  
|<span data-ttu-id="0da0b-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0da0b-396">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-396">String</span></span>|  
|<span data-ttu-id="0da0b-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-397">COLLATION_NAME</span></span>|<span data-ttu-id="0da0b-398">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-398">String</span></span>|  
|<span data-ttu-id="0da0b-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0da0b-400">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-400">String</span></span>|  
|<span data-ttu-id="0da0b-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0da0b-402">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-402">String</span></span>|  
|<span data-ttu-id="0da0b-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-403">DOMAIN_NAME</span></span>|<span data-ttu-id="0da0b-404">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-404">String</span></span>|  
|<span data-ttu-id="0da0b-405">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-405">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-406">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0da0b-407">Procédures</span><span class="sxs-lookup"><span data-stu-id="0da0b-407">Procedures</span></span>  
  
|<span data-ttu-id="0da0b-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-408">ColumnName</span></span>|<span data-ttu-id="0da0b-409">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0da0b-411">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-411">String</span></span>|  
|<span data-ttu-id="0da0b-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0da0b-413">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-413">String</span></span>|  
|<span data-ttu-id="0da0b-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="0da0b-415">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-415">String</span></span>|  
|<span data-ttu-id="0da0b-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0da0b-417">Int16</span><span class="sxs-lookup"><span data-stu-id="0da0b-417">Int16</span></span>|  
|<span data-ttu-id="0da0b-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0da0b-419">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-419">String</span></span>|  
|<span data-ttu-id="0da0b-420">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-420">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-421">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-421">String</span></span>|  
|<span data-ttu-id="0da0b-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0da0b-422">DATE_CREATED</span></span>|<span data-ttu-id="0da0b-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-423">DateTime</span></span>|  
|<span data-ttu-id="0da0b-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0da0b-424">DATE_MODIFIED</span></span>|<span data-ttu-id="0da0b-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="0da0b-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="0da0b-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="0da0b-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-427">ColumnName</span></span>|<span data-ttu-id="0da0b-428">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0da0b-430">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-430">String</span></span>|  
|<span data-ttu-id="0da0b-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0da0b-432">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-432">String</span></span>|  
|<span data-ttu-id="0da0b-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="0da0b-434">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-434">String</span></span>|  
|<span data-ttu-id="0da0b-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-435">COLUMN_NAME</span></span>|<span data-ttu-id="0da0b-436">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-436">String</span></span>|  
|<span data-ttu-id="0da0b-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-437">COLUMN_GUID</span></span>|<span data-ttu-id="0da0b-438">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-438">Guid</span></span>|  
|<span data-ttu-id="0da0b-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0da0b-439">COLUMN_PROPID</span></span>|<span data-ttu-id="0da0b-440">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-440">Int64</span></span>|  
|<span data-ttu-id="0da0b-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="0da0b-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="0da0b-442">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-442">Int64</span></span>|  
|<span data-ttu-id="0da0b-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="0da0b-444">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-444">Int64</span></span>|  
|<span data-ttu-id="0da0b-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0da0b-445">IS_NULLABLE</span></span>|<span data-ttu-id="0da0b-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-446">Boolean</span></span>|  
|<span data-ttu-id="0da0b-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-447">DATA_TYPE</span></span>|<span data-ttu-id="0da0b-448">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-448">Int32</span></span>|  
|<span data-ttu-id="0da0b-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-449">TYPE_GUID</span></span>|<span data-ttu-id="0da0b-450">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-450">Guid</span></span>|  
|<span data-ttu-id="0da0b-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0da0b-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0da0b-452">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-452">Int64</span></span>|  
|<span data-ttu-id="0da0b-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0da0b-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0da0b-454">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-454">Int64</span></span>|  
|<span data-ttu-id="0da0b-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0da0b-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0da0b-456">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-456">Int32</span></span>|  
|<span data-ttu-id="0da0b-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0da0b-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="0da0b-458">Int16</span><span class="sxs-lookup"><span data-stu-id="0da0b-458">Int16</span></span>|  
|<span data-ttu-id="0da0b-459">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-459">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-460">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-460">String</span></span>|  
|<span data-ttu-id="0da0b-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="0da0b-461">OVERLOAD</span></span>|<span data-ttu-id="0da0b-462">Int16</span><span class="sxs-lookup"><span data-stu-id="0da0b-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0da0b-463">Les vues</span><span class="sxs-lookup"><span data-stu-id="0da0b-463">Views</span></span>  
  
|<span data-ttu-id="0da0b-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-464">ColumnName</span></span>|<span data-ttu-id="0da0b-465">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-466">TABLE_CATALOG</span></span>|<span data-ttu-id="0da0b-467">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-467">String</span></span>|  
|<span data-ttu-id="0da0b-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="0da0b-469">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-469">String</span></span>|  
|<span data-ttu-id="0da0b-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-470">TABLE_NAME</span></span>|<span data-ttu-id="0da0b-471">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-471">String</span></span>|  
|<span data-ttu-id="0da0b-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="0da0b-473">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-473">String</span></span>|  
|<span data-ttu-id="0da0b-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="0da0b-474">CHECK_OPTION</span></span>|<span data-ttu-id="0da0b-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-475">Boolean</span></span>|  
|<span data-ttu-id="0da0b-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="0da0b-476">IS_UPDATABLE</span></span>|<span data-ttu-id="0da0b-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-477">Boolean</span></span>|  
|<span data-ttu-id="0da0b-478">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-478">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-479">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-479">String</span></span>|  
|<span data-ttu-id="0da0b-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0da0b-480">DATE_CREATED</span></span>|<span data-ttu-id="0da0b-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-481">DateTime</span></span>|  
|<span data-ttu-id="0da0b-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0da0b-482">DATE_MODIFIED</span></span>|<span data-ttu-id="0da0b-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0da0b-484">Index</span><span class="sxs-lookup"><span data-stu-id="0da0b-484">Indexes</span></span>  
  
|<span data-ttu-id="0da0b-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-485">ColumnName</span></span>|<span data-ttu-id="0da0b-486">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-487">TABLE_CATALOG</span></span>|<span data-ttu-id="0da0b-488">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-488">String</span></span>|  
|<span data-ttu-id="0da0b-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="0da0b-490">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-490">String</span></span>|  
|<span data-ttu-id="0da0b-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-491">TABLE_NAME</span></span>|<span data-ttu-id="0da0b-492">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-492">String</span></span>|  
|<span data-ttu-id="0da0b-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-493">INDEX_CATALOG</span></span>|<span data-ttu-id="0da0b-494">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-494">String</span></span>|  
|<span data-ttu-id="0da0b-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="0da0b-496">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-496">String</span></span>|  
|<span data-ttu-id="0da0b-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-497">INDEX_NAME</span></span>|<span data-ttu-id="0da0b-498">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-498">String</span></span>|  
|<span data-ttu-id="0da0b-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0da0b-499">PRIMARY_KEY</span></span>|<span data-ttu-id="0da0b-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-500">Boolean</span></span>|  
|<span data-ttu-id="0da0b-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0da0b-501">UNIQUE</span></span>|<span data-ttu-id="0da0b-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-502">Boolean</span></span>|  
|<span data-ttu-id="0da0b-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0da0b-503">CLUSTERED</span></span>|<span data-ttu-id="0da0b-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-504">Boolean</span></span>|  
|<span data-ttu-id="0da0b-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-505">TYPE</span></span>|<span data-ttu-id="0da0b-506">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-506">Int32</span></span>|  
|<span data-ttu-id="0da0b-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0da0b-507">FILL_FACTOR</span></span>|<span data-ttu-id="0da0b-508">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-508">Int32</span></span>|  
|<span data-ttu-id="0da0b-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0da0b-509">INITIAL_SIZE</span></span>|<span data-ttu-id="0da0b-510">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-510">Int32</span></span>|  
|<span data-ttu-id="0da0b-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="0da0b-511">NULLS</span></span>|<span data-ttu-id="0da0b-512">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-512">Int32</span></span>|  
|<span data-ttu-id="0da0b-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0da0b-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0da0b-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-514">Boolean</span></span>|  
|<span data-ttu-id="0da0b-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0da0b-515">AUTO_UPDATE</span></span>|<span data-ttu-id="0da0b-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-516">Boolean</span></span>|  
|<span data-ttu-id="0da0b-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0da0b-517">NULL_COLLATION</span></span>|<span data-ttu-id="0da0b-518">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-518">Int32</span></span>|  
|<span data-ttu-id="0da0b-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="0da0b-520">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-520">Int64</span></span>|  
|<span data-ttu-id="0da0b-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-521">COLUMN_NAME</span></span>|<span data-ttu-id="0da0b-522">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-522">String</span></span>|  
|<span data-ttu-id="0da0b-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-523">COLUMN_GUID</span></span>|<span data-ttu-id="0da0b-524">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-524">Guid</span></span>|  
|<span data-ttu-id="0da0b-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0da0b-525">COLUMN_PROPID</span></span>|<span data-ttu-id="0da0b-526">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-526">Int64</span></span>|  
|<span data-ttu-id="0da0b-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="0da0b-527">COLLATION</span></span>|<span data-ttu-id="0da0b-528">Int16</span><span class="sxs-lookup"><span data-stu-id="0da0b-528">Int16</span></span>|  
|<span data-ttu-id="0da0b-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="0da0b-529">CARDINALITY</span></span>|<span data-ttu-id="0da0b-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="0da0b-530">Decimal</span></span>|  
|<span data-ttu-id="0da0b-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="0da0b-531">PAGES</span></span>|<span data-ttu-id="0da0b-532">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-532">Int32</span></span>|  
|<span data-ttu-id="0da0b-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-533">FILTER_CONDITION</span></span>|<span data-ttu-id="0da0b-534">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-534">String</span></span>|  
|<span data-ttu-id="0da0b-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="0da0b-535">INTEGRATED</span></span>|<span data-ttu-id="0da0b-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="0da0b-537">Fournisseur Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="0da0b-537">Microsoft Jet OLE DB Provider</span></span>  

 <span data-ttu-id="0da0b-538">Le pilote Microsoft Jet OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="0da0b-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="0da0b-539">Tables</span><span class="sxs-lookup"><span data-stu-id="0da0b-539">Tables</span></span>  
  
- <span data-ttu-id="0da0b-540">Colonnes</span><span class="sxs-lookup"><span data-stu-id="0da0b-540">Columns</span></span>  
  
- <span data-ttu-id="0da0b-541">Procédures</span><span class="sxs-lookup"><span data-stu-id="0da0b-541">Procedures</span></span>  
  
- <span data-ttu-id="0da0b-542">Les vues</span><span class="sxs-lookup"><span data-stu-id="0da0b-542">Views</span></span>  
  
- <span data-ttu-id="0da0b-543">Index</span><span class="sxs-lookup"><span data-stu-id="0da0b-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="0da0b-544">Tables</span><span class="sxs-lookup"><span data-stu-id="0da0b-544">Tables</span></span>  
  
|<span data-ttu-id="0da0b-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-545">ColumnName</span></span>|<span data-ttu-id="0da0b-546">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-547">TABLE_CATALOG</span></span>|<span data-ttu-id="0da0b-548">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-548">String</span></span>|  
|<span data-ttu-id="0da0b-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="0da0b-550">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-550">String</span></span>|  
|<span data-ttu-id="0da0b-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-551">TABLE_NAME</span></span>|<span data-ttu-id="0da0b-552">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-552">String</span></span>|  
|<span data-ttu-id="0da0b-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-553">TABLE_TYPE</span></span>|<span data-ttu-id="0da0b-554">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-554">String</span></span>|  
|<span data-ttu-id="0da0b-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-555">TABLE_GUID</span></span>|<span data-ttu-id="0da0b-556">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-556">Guid</span></span>|  
|<span data-ttu-id="0da0b-557">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-557">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-558">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-558">String</span></span>|  
|<span data-ttu-id="0da0b-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="0da0b-559">TABLE_PROPID</span></span>|<span data-ttu-id="0da0b-560">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-560">Int64</span></span>|  
|<span data-ttu-id="0da0b-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0da0b-561">DATE_CREATED</span></span>|<span data-ttu-id="0da0b-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-562">DateTime</span></span>|  
|<span data-ttu-id="0da0b-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0da0b-563">DATE_MODIFIED</span></span>|<span data-ttu-id="0da0b-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="0da0b-565">Colonnes</span><span class="sxs-lookup"><span data-stu-id="0da0b-565">Columns</span></span>  
  
|<span data-ttu-id="0da0b-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-566">ColumnName</span></span>|<span data-ttu-id="0da0b-567">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-568">TABLE_CATALOG</span></span>|<span data-ttu-id="0da0b-569">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-569">String</span></span>|  
|<span data-ttu-id="0da0b-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="0da0b-571">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-571">String</span></span>|  
|<span data-ttu-id="0da0b-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-572">TABLE_NAME</span></span>|<span data-ttu-id="0da0b-573">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-573">String</span></span>|  
|<span data-ttu-id="0da0b-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-574">COLUMN_NAME</span></span>|<span data-ttu-id="0da0b-575">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-575">String</span></span>|  
|<span data-ttu-id="0da0b-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-576">COLUMN_GUID</span></span>|<span data-ttu-id="0da0b-577">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-577">Guid</span></span>|  
|<span data-ttu-id="0da0b-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0da0b-578">COLUMN_PROPID</span></span>|<span data-ttu-id="0da0b-579">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-579">Int64</span></span>|  
|<span data-ttu-id="0da0b-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="0da0b-581">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-581">Int64</span></span>|  
|<span data-ttu-id="0da0b-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="0da0b-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="0da0b-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-583">Boolean</span></span>|  
|<span data-ttu-id="0da0b-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="0da0b-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="0da0b-585">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-585">String</span></span>|  
|<span data-ttu-id="0da0b-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="0da0b-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="0da0b-587">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-587">Int64</span></span>|  
|<span data-ttu-id="0da0b-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="0da0b-588">IS_NULLABLE</span></span>|<span data-ttu-id="0da0b-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-589">Boolean</span></span>|  
|<span data-ttu-id="0da0b-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-590">DATA_TYPE</span></span>|<span data-ttu-id="0da0b-591">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-591">Int32</span></span>|  
|<span data-ttu-id="0da0b-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-592">TYPE_GUID</span></span>|<span data-ttu-id="0da0b-593">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-593">Guid</span></span>|  
|<span data-ttu-id="0da0b-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0da0b-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="0da0b-595">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-595">Int64</span></span>|  
|<span data-ttu-id="0da0b-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="0da0b-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="0da0b-597">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-597">Int64</span></span>|  
|<span data-ttu-id="0da0b-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0da0b-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="0da0b-599">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-599">Int32</span></span>|  
|<span data-ttu-id="0da0b-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="0da0b-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="0da0b-601">Int16</span><span class="sxs-lookup"><span data-stu-id="0da0b-601">Int16</span></span>|  
|<span data-ttu-id="0da0b-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="0da0b-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="0da0b-603">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-603">Int64</span></span>|  
|<span data-ttu-id="0da0b-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="0da0b-605">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-605">String</span></span>|  
|<span data-ttu-id="0da0b-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="0da0b-607">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-607">String</span></span>|  
|<span data-ttu-id="0da0b-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="0da0b-609">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-609">String</span></span>|  
|<span data-ttu-id="0da0b-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="0da0b-611">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-611">String</span></span>|  
|<span data-ttu-id="0da0b-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="0da0b-613">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-613">String</span></span>|  
|<span data-ttu-id="0da0b-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-614">COLLATION_NAME</span></span>|<span data-ttu-id="0da0b-615">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-615">String</span></span>|  
|<span data-ttu-id="0da0b-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="0da0b-617">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-617">String</span></span>|  
|<span data-ttu-id="0da0b-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="0da0b-619">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-619">String</span></span>|  
|<span data-ttu-id="0da0b-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-620">DOMAIN_NAME</span></span>|<span data-ttu-id="0da0b-621">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-621">String</span></span>|  
|<span data-ttu-id="0da0b-622">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-622">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-623">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="0da0b-624">Procédures</span><span class="sxs-lookup"><span data-stu-id="0da0b-624">Procedures</span></span>  
  
|<span data-ttu-id="0da0b-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-625">ColumnName</span></span>|<span data-ttu-id="0da0b-626">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="0da0b-628">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-628">String</span></span>|  
|<span data-ttu-id="0da0b-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="0da0b-630">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-630">String</span></span>|  
|<span data-ttu-id="0da0b-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="0da0b-632">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-632">String</span></span>|  
|<span data-ttu-id="0da0b-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="0da0b-634">Int16</span><span class="sxs-lookup"><span data-stu-id="0da0b-634">Int16</span></span>|  
|<span data-ttu-id="0da0b-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="0da0b-636">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-636">String</span></span>|  
|<span data-ttu-id="0da0b-637">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-637">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-638">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-638">String</span></span>|  
|<span data-ttu-id="0da0b-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0da0b-639">DATE_CREATED</span></span>|<span data-ttu-id="0da0b-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-640">DateTime</span></span>|  
|<span data-ttu-id="0da0b-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0da0b-641">DATE_MODIFIED</span></span>|<span data-ttu-id="0da0b-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="0da0b-643">Les vues</span><span class="sxs-lookup"><span data-stu-id="0da0b-643">Views</span></span>  
  
|<span data-ttu-id="0da0b-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-644">ColumnName</span></span>|<span data-ttu-id="0da0b-645">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-646">TABLE_CATALOG</span></span>|<span data-ttu-id="0da0b-647">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-647">String</span></span>|  
|<span data-ttu-id="0da0b-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="0da0b-649">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-649">String</span></span>|  
|<span data-ttu-id="0da0b-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-650">TABLE_NAME</span></span>|<span data-ttu-id="0da0b-651">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-651">String</span></span>|  
|<span data-ttu-id="0da0b-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="0da0b-653">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-653">String</span></span>|  
|<span data-ttu-id="0da0b-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="0da0b-654">CHECK_OPTION</span></span>|<span data-ttu-id="0da0b-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-655">Boolean</span></span>|  
|<span data-ttu-id="0da0b-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="0da0b-656">IS_UPDATABLE</span></span>|<span data-ttu-id="0da0b-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-657">Boolean</span></span>|  
|<span data-ttu-id="0da0b-658">Description</span><span class="sxs-lookup"><span data-stu-id="0da0b-658">DESCRIPTION</span></span>|<span data-ttu-id="0da0b-659">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-659">String</span></span>|  
|<span data-ttu-id="0da0b-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="0da0b-660">DATE_CREATED</span></span>|<span data-ttu-id="0da0b-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-661">DateTime</span></span>|  
|<span data-ttu-id="0da0b-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="0da0b-662">DATE_MODIFIED</span></span>|<span data-ttu-id="0da0b-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="0da0b-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="0da0b-664">Index</span><span class="sxs-lookup"><span data-stu-id="0da0b-664">Indexes</span></span>  
  
|<span data-ttu-id="0da0b-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="0da0b-665">ColumnName</span></span>|<span data-ttu-id="0da0b-666">DataType</span><span class="sxs-lookup"><span data-stu-id="0da0b-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="0da0b-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-667">TABLE_CATALOG</span></span>|<span data-ttu-id="0da0b-668">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-668">String</span></span>|  
|<span data-ttu-id="0da0b-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="0da0b-670">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-670">String</span></span>|  
|<span data-ttu-id="0da0b-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-671">TABLE_NAME</span></span>|<span data-ttu-id="0da0b-672">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-672">String</span></span>|  
|<span data-ttu-id="0da0b-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="0da0b-673">INDEX_CATALOG</span></span>|<span data-ttu-id="0da0b-674">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-674">String</span></span>|  
|<span data-ttu-id="0da0b-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="0da0b-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="0da0b-676">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-676">String</span></span>|  
|<span data-ttu-id="0da0b-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-677">INDEX_NAME</span></span>|<span data-ttu-id="0da0b-678">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-678">String</span></span>|  
|<span data-ttu-id="0da0b-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="0da0b-679">PRIMARY_KEY</span></span>|<span data-ttu-id="0da0b-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-680">Boolean</span></span>|  
|<span data-ttu-id="0da0b-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="0da0b-681">UNIQUE</span></span>|<span data-ttu-id="0da0b-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-682">Boolean</span></span>|  
|<span data-ttu-id="0da0b-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="0da0b-683">CLUSTERED</span></span>|<span data-ttu-id="0da0b-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-684">Boolean</span></span>|  
|<span data-ttu-id="0da0b-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="0da0b-685">TYPE</span></span>|<span data-ttu-id="0da0b-686">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-686">Int32</span></span>|  
|<span data-ttu-id="0da0b-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="0da0b-687">FILL_FACTOR</span></span>|<span data-ttu-id="0da0b-688">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-688">Int32</span></span>|  
|<span data-ttu-id="0da0b-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="0da0b-689">INITIAL_SIZE</span></span>|<span data-ttu-id="0da0b-690">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-690">Int32</span></span>|  
|<span data-ttu-id="0da0b-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="0da0b-691">NULLS</span></span>|<span data-ttu-id="0da0b-692">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-692">Int32</span></span>|  
|<span data-ttu-id="0da0b-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="0da0b-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="0da0b-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-694">Boolean</span></span>|  
|<span data-ttu-id="0da0b-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="0da0b-695">AUTO_UPDATE</span></span>|<span data-ttu-id="0da0b-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-696">Boolean</span></span>|  
|<span data-ttu-id="0da0b-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="0da0b-697">NULL_COLLATION</span></span>|<span data-ttu-id="0da0b-698">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-698">Int32</span></span>|  
|<span data-ttu-id="0da0b-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="0da0b-700">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-700">Int64</span></span>|  
|<span data-ttu-id="0da0b-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="0da0b-701">COLUMN_NAME</span></span>|<span data-ttu-id="0da0b-702">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-702">String</span></span>|  
|<span data-ttu-id="0da0b-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="0da0b-703">COLUMN_GUID</span></span>|<span data-ttu-id="0da0b-704">Guid</span><span class="sxs-lookup"><span data-stu-id="0da0b-704">Guid</span></span>|  
|<span data-ttu-id="0da0b-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="0da0b-705">COLUMN_PROPID</span></span>|<span data-ttu-id="0da0b-706">Int64</span><span class="sxs-lookup"><span data-stu-id="0da0b-706">Int64</span></span>|  
|<span data-ttu-id="0da0b-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="0da0b-707">COLLATION</span></span>|<span data-ttu-id="0da0b-708">Int16</span><span class="sxs-lookup"><span data-stu-id="0da0b-708">Int16</span></span>|  
|<span data-ttu-id="0da0b-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="0da0b-709">CARDINALITY</span></span>|<span data-ttu-id="0da0b-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="0da0b-710">Decimal</span></span>|  
|<span data-ttu-id="0da0b-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="0da0b-711">PAGES</span></span>|<span data-ttu-id="0da0b-712">Int32</span><span class="sxs-lookup"><span data-stu-id="0da0b-712">Int32</span></span>|  
|<span data-ttu-id="0da0b-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="0da0b-713">FILTER_CONDITION</span></span>|<span data-ttu-id="0da0b-714">String</span><span class="sxs-lookup"><span data-stu-id="0da0b-714">String</span></span>|  
|<span data-ttu-id="0da0b-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="0da0b-715">INTEGRATED</span></span>|<span data-ttu-id="0da0b-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="0da0b-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0da0b-717">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0da0b-717">See also</span></span>

- [<span data-ttu-id="0da0b-718">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0da0b-718">ADO.NET Overview</span></span>](ado-net-overview.md)
