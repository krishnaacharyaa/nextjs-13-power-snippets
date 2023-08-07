# All Snippets

> Each Snippet belong to a category of prefix. Same prefix can be used for both `typescript` and `javascript` files, `$` represents each step after `tab`,

## Snippet Categories

| Category                      | Prefix Group | Description                                                                                                                                   |
| ----------------------------- | :----------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
| [Pages](#pages)               |   **`np`**   | Quickly generate dynamic, statically fetched, or revalidated pages with various data fetching methods (`axios`/`fetch`) and parameter options |
| [Route Handlers](#routes)     |   **`nr`**   | Create route handler functions for different HTTP methods (`GET`, `POST`, `PUT`, `DELETE`) with built-in error handling                       |
| [Actions](#actions)           |   **`na`**   | Utilize prebuilt action templates to seamlessly interact with API routes using either `axios` or `fetch`                                      |
| [Functions](#functions)       |   **`nf`**   | Leverage templates for generating Image, Static, and Dynamic Metadata, as well as static params functions                                     |
| [Components](#components)     |   **`nc`**   | Get the component templates for loading, notfound, error, image, and many more                                                                |
| [Imports](#imports)           |   **`ni`**   | Import a wide range of Next.js modules and utilities with ease                                                                                |
| [Declarations](#declarations) |   **`nd`**   | Quickly declare variables with available templates                                                                                            |

---

## Snippets Description

<a name="pages"></a>

### Next.js Page - `np`

<table>
<tr>
<td> Prefix </td> <td> Body </td>
</tr>
<tr>
<td> <code>npfetchStatic</code> </td>
<td>

```tsx
async function ${1:getData}() {
  const res = await fetch("${2:https://...}");

  if (!res.ok) {
    throw new Error("Failed to fetch data");
  }

  return res.json();
}

export default async function Page() {
  const data = await ${1:getData}();

  return <main>${3}</main>;
}
```

</td>
</tr>
<tr>
<td> <code>npfetchRevalidate</code> </td>
<td>

```tsx
async function ${1:getData}() {
  const res = await fetch("${2:https://...}", { next: { revalidate: ${3:3600} } });

  if (!res.ok) {
    throw new Error("Failed to fetch data");
  }

  return res.json();
}

export default async function Page() {
  const data = await ${1:getData}();

  return <main>${4}</main>;
}
```

</td>
</tr>
<tr>
<td> <code>npfetchdynamic</code> </td>
<td>

```tsx
async function ${1:getData}() {
  const res = await fetch("${2:https://...}", { cache: "no-store" });

  if (!res.ok) {
    throw new Error("Failed to fetch data");
  }

  return res.json();
}

export default async function Page() {
  const data = await ${1:getData}();

  return <main>${3}</main>;
}
```

</td>
</tr>
<tr>
<td> <code>npaxiosStatic</code> </td>
<td>

```ts
import axios from "axios";

async function ${1:getData}() {
  try {
    const response = await axios.get(`${2:https://...}`);
    const {result} = response.data;
    return result;
  } catch (error: any) {
    throw new Error("Failed to fetch data");
  }
}

export default async function Page() {
  const data = await ${1:getData}();

  return <main>${4}</main>;
}
```

</td>
</tr>
<tr>
<td> <code>npaxiosDynamic</code> </td>
<td>

```tsx
import axios from "axios";

export const fetchCache = "force-no-store";

async function ${1:getData}() {
  try {
    const response = await axios.get(`${2:https://...}`);
    const  {result} = response.data;
    return result;
  } catch (error: any) {
    throw new Error("Failed to fetch data");
  }
}

export default async function Page() {
  const data = await ${1:getData}();

  return <main>${4}</main>;
}
```

</td>
</tr>
<tr>
<td> <code>npaxiosRevalidate</code> </td>
<td>

```tsx
import axios from "axios";

export const revalidate = ${1:3600};

async function ${2:getData}() {
  try {
    const response = await axios.get(`${3:https://...}`);
    const { result } = response.data;
    return result;
  } catch (error: any) {
    throw new Error("Failed to fetch data");
  }
}

export default async function Page() {
  const data = await ${2:getData}();

  return <main>${5}</main>;
}
```

</td>
</tr>
<tr>
<td> <code>npparams</code> </td>
<td>

```tsx
export default function Page({ params }: {
  params: { ${1:id}: string };
}) {
  const ${1:id} = params.${1:id};
  return (
    <main>
      ${2}
    </main>
  );
}
```

</td>
</tr>
<tr>
<td> <code>npsearchParams</code> </td>
<td>

```tsx
export default function Page({
  searchParams,
}: {
  searchParams: { ${1:id}: ${2:string} };
}) {
  const ${1:id} = searchParams.${1:id};
  return <main>${3}</main>;
}
```

</td>
</tr>
<tr>
<td> <code>npparamsSearchParams</code> </td>
<td>

```tsx
export default function Page({
  params,
  searchParams,
}: {
  params: { ${1:paramId}: ${2:string} };
  searchParams: { ${3:searchId}: ${4:string} };
}) {
  const ${1:paramId} = params.${1:paramId};
  const ${3:searchId} = searchParams.${3:searchId};
  return <main>${5}</main>;
}
```

</td>
</tr>
<tr>
<td> <code>np</code> </td>
<td>

```tsx
export default function Page() {
	return <main>${1}</main>;
}
```

</td>
</tr>
<tr>
<td> <code>npasync</code> </td>
<td>

```tsx
async function ${1:customFunction}() {
  ${2}
}

export default async function Page() {
  const data = await ${1:customFunction}();
  return <main>${3}</main>;
}
```

</td>
</tr>
<tr>
<td> <code>nplayout</code> </td>
<td>

```tsx
export default function ${1:Layout}({ children }: {
  children: React.ReactNode;
}) {
  return (
    <section>
      {children}
    </section>
  );
}
```

</td>
</tr>
</table>

<a name="routes"></a>

### Next.js Route Handler - `nr`

<table>
<tr>
<td> Prefix </td> <td> Body </td>
</tr>
<tr>
<td> <code>nrget</code> </td>
<td>

```tsx
import { NextResponse } from "next/server";

export async function GET() {
  try {
    const ${2:result} = await ${1:fetchData()};
    return NextResponse.json({ message: "OK", ${2:result} }, { status: 200 });
  } catch (error) {
    return NextResponse.json({ message: "Error", error }, { status: 500 });
  }
}
```

</td>
</tr>
<tr>
<td> <code>nrgetSearchParams</code> </td>
<td>

```tsx
import { NextRequest, NextResponse } from "next/server";

export async function GET(request: NextRequest) {
  const ${1:id} = request.nextUrl.searchParams.get("${1:id}");
  try {
    const result = await ${2:fetchData(${1:id})};
    return NextResponse.json({ message: "OK", result }, { status: 200 });
  } catch (error) {
    return NextResponse.json({ message: "Error", error }, { status: 500 });
  }
}
```

</td>
</tr>
<tr>
<td> <code>nrgetParams</code> </td>
<td>

```tsx
import { NextRequest, NextResponse } from "next/server";

export async function GET(request: NextRequest, {params}: any) {
  const ${1:id} = params.${1:id};
  try {
    const result = await ${2:fetchData(${1:id})};
    return NextResponse.json({ message: "OK", result }, { status: 200 });
  } catch (error) {
    return NextResponse.json({ message: "Error", error }, { status: 500 });
  }
}
```

</td>
</tr>
<tr>
<td> <code>nrpost</code> </td>
<td>

```tsx
import { NextRequest, NextResponse } from "next/server";

export async function POST(request: NextRequest) {
  const ${1:body} = await request.json();
  try {
    const result = await ${2:saveData(${1:body})};
    return NextResponse.json({ message: "OK", result }, { status: 201 });
  } catch (error) {
    return NextResponse.json({ message: "Error", error }, { status: 500 });
  }
}
```

</td>
</tr>
<tr>
<td> <code>nrput</code> </td>
<td>

```tsx
import { NextRequest, NextResponse } from "next/server";

export async function PUT(request: NextRequest, {params}: any) {
  const ${1:id} = params.id;
  const ${2:body} = await request.json();
  try {
    const result = await ${3:updateData(${1:id}, ${2:body})};
    return NextResponse.json({ message: "OK", result }, { status: 200 });
  } catch (error) {
    return NextResponse.json({ message: "Error", error }, { status: 500 });
  }
}
```

</td>
</tr>
<tr>
<td> <code>nrdelete</code> </td>
<td>

```tsx
import { NextRequest, NextResponse } from "next/server";

export async function DELETE(request: NextRequest, {params}: any) {
  const ${1:id} = params.${1:id};
  try {
    const result = await ${2:deleteData(${1:id})};
    return NextResponse.json({ message: "OK", result }, { status: 200 });
  } catch (error) {
    return NextResponse.json({ message: "Error", error }, { status: 500 });
  }
}
```

</td>
</tr>
</table>

<a name="actions"></a>

### Next.js Actions - `na`

<table>
<tr>
<td> Prefix </td> <td> Body </td>
</tr>
<tr>
<td> <code>naaxiosPost</code> </td>
<td>

```tsx
import axios from "axios";

export async function ${1:axiosPostFunction}(body: ${2:Object}) {
  try {
    const response = await axios.post(`${3:https://...}`, {
      body,
    });
    const { ${4:result} } = response.data;
    return ${4:result};
  } catch (error) {
    throw new Error("${5:Axios Post Error :("});
  }
}
```

</td>
</tr>
<tr>
<td> <code>naaxiosGet</code> </td>
<td>

```tsx
import axios from "axios";

export async function ${1:axiosGetFunction}() {
  try {
    const response = await axios.get(`${2:https://:...}`);
    const { ${3:result} } = response.data;
    return ${3:result};
  } catch (error: any) {
    throw new Error("${4:Axios Get Error :("});
  }
}
```

</td>
</tr>
<tr>
<td> <code>naaxiosPut</code> </td>
<td>

```tsx
import axios from "axios";

export async function ${1:axiosPutFunction}(id: string, body: ${2:Object}) {
  try {
    const response = await axios.put(`${3:https://}`+id, {
      body,
    });
    const { ${4:result} } = response.data;
    return ${4:result};
  } catch (error: any) {
    throw new Error("${5:Axios Put Error :("});
  }
}
```

</td>
</tr>
<tr>
<td> <code>naaxiosDelete</code> </td>
<td>

```tsx
import axios from "axios";

export async function ${1:axiosDeleteFunction}(id: string) {
  try {
    const response = await axios.delete(`${2:https://...}` + id);
    const { ${3:result} } = response.data;
    return ${3:result};
  } catch (error: any) {
    throw new Error("${4:Axios Delete Error :("});
  }
}
```

</td>
</tr>
<tr>
<td> <code>nafetchGet</code> </td>
<td>

```tsx
export async function ${1:fetchGetFunction}() {
  try {
    const response = await fetch(`${2:https://:...}`, {
      method: "GET",
      headers: {
        "Content-Type": "application/json",
      },
    });

    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    return response.json();
  } catch (error) {
    console.error("${3:Fetch GET error:}", error);
    throw error;
  }
}
```

</td>
</tr>
<tr>
<td> <code>nafetchPost</code> </td>
<td>

```tsx
export async function ${1:fetchPostFunction}(body: ${2:Object}) {
  try {
    const response = await fetch(`${3:https://:...}`, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(body),
    });

    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    return response.json();
  } catch (error) {
    console.error("${4:Fetch POST error:}", error);
    throw error;
  }
}
```

</td>
</tr>
<tr>
<td> <code>nafetchPut</code> </td>
<td>

```tsx
export async function ${1:fetchPutFunction}(id: string, body: ${2:Object}) {
  try {
    const response = await fetch(`${3:https://...}` + id, {
      method: "PUT",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(body),
    });

    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    return response.json();
  } catch (error) {
    console.error("${4:Fetch PUT error:}", error);
    throw error;
  }
}
```

</td>
</tr>
<tr>
<td> <code>nafetchDelete</code> </td>
<td>

```tsx
export async function ${1:fetchDeleteFunction}(id: string) {
  try {
    const response = await fetch(`${2:https://...}` + id, {
      method: "DELETE",
    });

    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    return response.json();
  } catch (error) {
    console.error("${3:Fetch DELETE error:}",

 error);
    throw error;
  }
}
```

</td>
</tr>
</table>

<a name="functions"></a>

### Next.js Functions - `nf`

<table>
<tr>
<td> Prefix </td> <td> Body </td>
</tr>
<tr>
<td> <code>nf</code> </td>
<td>

```tsx
export function ${1:functionName}() {
  ${2}
}
```

</td>
</tr>
<tr>
<td> <code>nfdefaultExport</code> </td>
<td>

```tsx
export default function ${1:functionName}() {
  ${2}
}
```

</td>
</tr>
<tr>
<td> <code>nfgimageMetaData</code> </td>
<td>

```tsx
export function ${1:generateImageMetadata}({
  params,
}: {
  params: { ${2:} }
}) {
  <div>
     ${3:Content here}
 </div>
}
```

</td>
</tr>
<tr>
<td> <code>nfgstaticMetadata</code> </td>
<td>

```tsx
import { Metadata } from "next";

export const metadata: Metadata = {
	title: "${1:Title}",
};
```

</td>
</tr>
<tr>
<td> <code>nfgdynamicMetaData</code> </td>
<td>

```tsx
import { Metadata } from 'next';

export async function generateMetadata({
  params,
}: {
  params: { ${1:name}: string };
}) : Promise<Metadata> {
  return {
    title: params.${1:name},
  };
}
```

</td>
</tr>
<tr>
<td> <code>nfgstaticParams</code> </td>
<td>

```tsx
export async function generateStaticParams() {
  const ${1:dataList} = await fetch('${2:https://...}').then((res) => res.json());

  return ${1:dataList}.map((data:${3:Object}) => ({
    ${4:param}: data.${4:param},
  }));
}
```

</td>
</tr>
</table>

<a name="components"></a>

### Next.js Component - `nc`

<table style="width: 100%;">
<tr>
<td> Prefix </td> <td> Body </td>
</tr>
<tr>
<td> <code>ncloading</code> </td>
<td>

```tsx
export default function ${1:Loading}() {
  return <p>${2:Loading...}</p>;
}
```

</td>
</tr>
<tr>
<td> <code>ncnotFound</code> </td>
<td>

```tsx
export default function ${1:NotFound}() {
  return (
    <div>
      <h2>${2:Not Found}</h2>
    </div>
  );
}
```

</td>
</tr>
<tr>
<td> <code>ncerror</code> </td>
<td>

```tsx
'use client';

export default function ${1:Error}({
  error,
  reset,
}: {
  error: Error & { digest?: string };
  reset: () => void;
}) {
  return (
    <div>
      Error: {error.message}
      <button onClick={() => reset()}>Try again</button>
    </div>
  );
}
```

</td>
</tr>
<tr>
<td> <code>ncimage</code> </td>
<td>

```tsx
import Image from 'next/image';

export default function ${1:Page}() {
  return (
    <Image
      src="${2}"
      width={$3}
      height={$4}
      alt="${5}"
    />
  );
}
```

</td>
</tr>
<tr>
<td> <code>nclink</code> </td>
<td>

```tsx
import Link from 'next/link';

export default function ${1:Page}() {
  return (
    <Link href="/${2}">
      ${3:Link Text}
    </Link>
  );
}
```

</td>
</tr>
<tr>
<td> <code>ncscript</code> </td>
<td>

```tsx
import Script from 'next/script';

export default function ${1:Page}() {
  return (
    <>
      <Script src="${2}" />
    </>
  );
}
```

</td>
</tr>
</table>

<a name="declarations"></a>

### Next.js Declarations - `nd`

<table style="width: 100%;">
<tr>
<th>Prefix</th>
<th>Body</th>
</tr>
<tr>
<td><code>ndfetchStaticData</code></td>
<td>
  
```tsx
const ${1:staticData} = await fetch("${2:https://...}", { cache: 'force-cache' });
```

</td>
</tr>
<tr>
<td><code>ndfetchDynamicData</code></td>
<td>
  
```tsx
const ${1:dynamicData} = await fetch("${2:https://...}", { cache: 'no-store' });
```

</td>
</tr>
<tr>
<td><code>ndfetchRevalidatedData</code></td>
<td>
  
```tsx
const ${1:revalidatedData} = await fetch("${2:https://...}", {
  next: { revalidate: ${3:10} },
});
```

</td>
</tr>
</table>

<a name="imports"></a>

### Next.js Imports - `ni`

<table style="width: 100%;">
  <tr>
    <th>Prefix</th>
    <th>Body</th>
  </tr>
  <tr>
    <td><code>niuseRouter</code></td>
    <td>

```tsx
import { useRouter } from "next/navigation";
```

  </td>
  </tr>
  <tr>
    <td><code>nicookies</code></td>
    <td>

```tsx
import { cookies } from "next/headers";
```

  </td>
  </tr>
  <tr>
    <td><code>nidraftMode</code></td>
    <td>

```tsx
import { draftMode } from "next/headers";
```

  </td>
  </tr>
  <tr>
    <td><code>niheaders</code></td>
    <td>

```tsx
import { headers } from "next/headers";
```

   </td>
  </tr>
  <tr>
    <td><code>niimageResponse</code></td>
    <td>

```tsx
import { ImageResponse } from "next/server";
```

   </td>
  </tr>
  <tr>
    <td><code>niresponse</code></td>
    <td>

```tsx
import { NextResponse } from "next/server";
```

   </td>
  </tr>
  <tr>
    <td><code>nirequest</code></td>
    <td>

```tsx
import { NextRequest } from "next/server";
```

   </td>
  </tr>
  <tr>
    <td><code>ninotFound</code></td>
    <td>

```tsx
import { notFound } from "next/navigation";
```

   </td>
  </tr>
  <tr>
    <td><code>niredirect</code></td>
    <td>

```tsx
import { redirect } from "next/navigation";
```

   </td>
  </tr>
  <tr>
    <td><code>nirevalidateTag</code></td>
    <td>

```tsx
import { revalidateTag } from "next/cache";
```

   </td>
  </tr>
  <tr>
    <td><code>nirevalidatePath</code></td>
    <td>

```tsx
import { revalidatePath } from "next/cache";
```

   </td>
  </tr>
  <tr>
    <td><code>niuseParams</code></td>
    <td>

```tsx
import { useParams } from "next/navigation";
```

   </td>
  </tr>
  <tr>
    <td><code>niusePathname</code></td>
    <td>

```tsx
import { usePathname } from "next/navigation";
```

   </td>
  </tr>
  <tr>
    <td><code>niuseReportWebVitals</code></td>
    <td>

```tsx
import { useReportWebVitals } from "next/web-vitals";
```

   </td>
  </tr>
  <tr>
    <td><code>niuseSearchParams</code></td>
    <td>

```tsx
import { useSearchParams } from "next/navigation";
```

   </td>
  </tr>
  <tr>
    <td><code>niuseSelectedLayoutSegment</code></td>
    <td>

```tsx
import { useSelectedLayoutSegment } from "next/navigation";
```

   </td>
  </tr>
  <tr>
    <td><code>niuseSelectedLayoutSegments</code></td>
    <td>

```tsx
import { useSelectedLayoutSegments } from "next/navigation";
```

   </td>
  </tr>
</table>
