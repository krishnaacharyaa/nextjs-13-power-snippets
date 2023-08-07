# Next.js 13+ Power Snippets | TypeScript/JavaScript

Supercharge your Next.js development with a collection of powerful and time-saving code snippets specifically tailored both in TypeScript and JavaScript

## Overview

This extension offers a comprehensive collection of code snippets that cover a wide range of scenarios, allowing you to effortlessly enhance your productivity and build stunning Next.js applications.

## Features

- **Effortless Usage:** Each snippet comes with an intuitive and memorable prefix, ensuring you can quickly insert the desired code.
- **Organized Sections:** Snippets are thoughtfully grouped into categories for quick access.
- **JavaScript & TypeScript:** Enjoy seamless compatibility with both JavaScript and TypeScript, catering to your coding preferences.
- **Next.js 13+ Optimized:** These snippets are tailored for Next.js 13+, ensuring you have the latest and most efficient tools at your fingertips.

## Snippet Categories

| Category       | Prefix Group | Description                                                                                                                                   |
| -------------- | :----------: | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Pages          |   **`np`**   | Quickly generate dynamic, statically fetched, or revalidated pages with various data fetching methods (`axios`/`fetch`) and parameter options |
| Route Handlers |   **`nr`**   | Create route handler functions for different HTTP methods (`GET`, `POST`, `PUT`, `DELETE`) with built-in error handling                       |
| Actions        |   **`na`**   | Utilize prebuilt action templates to seamlessly interact with API routes using either `axios` or `fetch`                                      |
| Functions      |   **`nf`**   | Leverage templates for generating Image, Static, and Dynamic Metadata, as well as static params functions                                     |
| Components     |   **`nc`**   | Get the component templates for loading, notfound, error, image, and many more                                                                |
| Imports        |   **`ni`**   | Import a wide range of Next.js modules and utilities with ease                                                                                |
| Declarations   |   **`nd`**   | Quickly declare variables with available templates                                                                                            |

## Usage

1. Install the Next.js Code Snippets Extension in your code editor.
2. Open a `.js|.jsx` or `.ts|.tsx` file in your Next.js project.
3. Start typing the snippet prefix to trigger auto-suggestions.
4. Select the desired snippet and press `Enter` to insert the code.

## Handy Snippets

### Next.js Page - `np`

1. **`np`** - Next.js Page: Default

```tsx
export default function Page() {
	return <main>{/* Your content here */}</main>;
}
```

2. **`npasync`** - Next.js Page: Async Function

```tsx
async function customFunction() {
	/* Your code here */
}

export default async function Page() {
	const data = await customFunction();
	return <main>{/* Your content here */}</main>;
}
```

3. **`npfetchStatic`** - Next.js Page: Fetch default (staticData)

```jsx
async function getData() {
	const res = await fetch("https://...");

	if (!res.ok) {
		throw new Error("Failed to fetch data");
	}

	return res.json();
}

export default async function Page() {
	const data = await getData();

	return <main>{/* Your content here */}</main>;
}
```

### Next.js Route Handler - `nr`

1. **`nrpost`** - Next.js Route Handler: Default POST Method

```tsx
import { NextRequest, NextResponse } from "next/server";

export async function POST(request: NextRequest) {
	const body = await request.json();
	try {
		const result = await saveData(body);
		return NextResponse.json({ message: "OK", result }, { status: 201 });
	} catch (error) {
		return NextResponse.json({ message: "Error", error }, { status: 500 });
	}
}
```

2. **`nrgetSearchParams`** - Next.js Route Handler: GET() with searchParams

```tsx
import { NextRequest, NextResponse } from "next/server";

export async function GET(request: NextRequest) {
	const id = request.nextUrl.searchParams.get("id");
	try {
		const result = await fetchData(id);
		return NextResponse.json({ message: "OK", result }, { status: 200 });
	} catch (error) {
		return NextResponse.json({ message: "Error", error }, { status: 500 });
	}
}
```

### Next.js Action - `na`

1. **`nafetchGet`** - Next.js Action: Fetch GET Request

```tsx
export async function fetchGetFunction() {
	try {
		const response = await fetch("https://...", {
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
		console.error("Fetch GET error:", error);
		throw error;
	}
}
```

2. **`naaxiosGet`** - Next.js Action: Axios GET request

```tsx
import axios from "axios";

export async function axiosGetFunction() {
	try {
		const response = await axios.get("https://...");
		const { result } = response.data;
		return result;
	} catch (error: any) {
		throw new Error("Axios Get Error :(");
	}
}
```

### Next.js Function - `nf`

1. **`nf`** - Next.js Function: Basic

```tsx
export function ${1:functionName}() {
  /* Your code here */
}
```

2. **`nfdefaultExport`** - Next.js Function: Default Export

```tsx
export default function ${1:functionName}() {
  /* Your code here */
}
```

3. **`nfgstaticParams`** - Next.js Function: generateStaticParams

```tsx
export async function generateStaticParams() {
	const dataList = await fetch("https://...").then((res) => res.json());

	return dataList.map((data: Object) => ({
		param: data.param,
	}));
}
```

### Next.js Component - `nc`

1. **`ncloading`** - Next.js Component: Loading

```tsx
export default function Loading() {
	return <p>Loading...</p>;
}
```

## Snippets

Kindly find all the snippets [here](./documentation/snippets.md)

## Feedback and Contributions

We're dedicated to improving this extension and making it even more useful for the Next.js community. If you have found a bug, have suggestions, or want to contribute new snippets, feel free to reach out on [GitHub](https://github.com/krishnaacharyaa/nextjs-13-power-snippets).

---

Thank you for choosing the Next.js Code Snippets Extension! Happy coding!
