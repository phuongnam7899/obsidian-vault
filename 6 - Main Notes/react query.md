2024-11-09 15:35

Tags: [[ReactJS]]

---

# Full docs
- https://react-query.tanstack.com/
# Installation
```bash
	npm i react-query
```

# Quick view
## Client (**QueryClient**):
```js
	const queryClient = new QueryClient()
```

- Client provider (**QueryClientProvider**)
```js
function App() {
	return (
		<QueryClientProvider client={queryClient}>
		
			<InnerComponent />
		
		</QueryClientProvider>
	)
}
```

## Access the client to query/mutate
### Query
```js
 const queryClient = useQueryClient()
 const result = useQuery('query-key', fetchData)
 const { isLoading, isError, data, status, error, refetch } == result
```
#### Query key:
-  Simple text-only:  `"query-key"` is used for re-fetching, caching, and sharing your queries throughout application
-  Can be array: `['string', 1, { field: "value" }]`
#### Query functions
- Error handling: any errors thrown from function will be stored in `error`
#### Parallel queries
- When use multiple `useQuery()`, auto parallel
- When need dynamic parallel queries, use `useQuerries()`
```
 const userQueries = useQueries([
	 {
		queryKey: 'key1',
		queryFn: fetch1,
	 },
	 {
		queryKey: 'key2',
		queryFn: fetch2,
	 }
 ])
```
#### Dependent queries
- use `enabled` option:
```
 const result = useQuery('key', func, {
	 enabled: true,
 })
```
#### Query retry
- Default retries number = 3
- Custom retries number:
```js
	const result = useQuery('key', func, {
		 retry: 10,
	 });
	 
	 const result = useQuery('key', func, {
		 retry: true,
	 });
	 
	 const result = useQuery('key', func, {
		 retry: (failedCount, err) => {
			 return 1
		 },
	 })
```
- Retry delay: update when create client
```js
const queryClient = new QueryClient({
   defaultOptions: {
     queries: {
		 retryDelay: attemptIndex => Math.min(1000 * 2 ** attemptIndex, 30000),
	 },
	},
 })
```
#### Paginated
```js
 const [page, setPage] = useState(0)
 const { isPreviousData } = useQuery(['key', page], () => fetchProjects(page), { 
    keepPreviousData : true 
 });
```
#### Initial data
```js
const initialData = [1,2,3]
const result = useQuery('key', fetchData, {initialData: initialData,})
```
#### Prefetch
              
### Mutate
```js
 const queryClient = useQueryClient()

 const mutation = useMutation(postTodo, {
	 onSuccess: () => {
		// Invalidate and refetch
	    queryClient.invalidateQueries('todos')
	 },
 })
  return (<button onCLick={() => {
	 mutation.mutate({
        field: 'value',
        field2: 'value 2',
	 }
 }}>Query</button)
```


---
# References