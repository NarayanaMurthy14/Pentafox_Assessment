# Pentafox_Assessment
**1.Optimize the Waterfall**
React &amp; JavaScript Assessment
async function getUsers(userIds) {
  const requests = userIds.map(id =>
    fetch(`/users/${id}`).then(res => res.json())
  );

  return Promise.all(requests);
}

**2.The Recursive Tree**
function buildTree(comments) {
  const map = {};
  const result = [];
  comments.forEach(c => {
    map[c.id] = { ...c, children: [] };
  });
  comments.forEach(c => {
    if (c.parentId === null) {
      result.push(map[c.id]);
    } else {  map[c.parentId].children.push(map[c.id];
    }
    });
  return result;
}

****3. Reduse to Object ****
const result = orders.reduce((acc, order) => {
  acc[order.status] = (acc[order.status] || 0) + 1;
  return acc;
}, {});
console.log(result);

4.FIX THE STALE ALERT
import { useState, useRef, useEffect } from "react";
function App() {
  const [darkMode, setDarkMode] = useState(false);
  const darkModeRef = useRef(darkMode);
  useEffect(() => {
    darkModeRef.current = darkMode;
  }, [darkMode]);
  const handleStart = () => {
    setTimeout(() => {
      alert(`Dark Mode is: ${darkModeRef.current}`);
    }, 5000);
  };
  return (
    <div>
      <input
        type="checkbox"
        checked={darkMode}
        onChange={(e) => setDarkMode(e.target.checked)}
      />
      <button onClick={handleStart}>Start Timer</button>
    </div>
  );
}

**5. Stop the Infinite Loop**
const fetchUser = useCallback(async () => {
  const res = await fetch(`/api/users/${userId}`);
  setUser(await res.json());
}, [userId]);

useEffect(() => {
  fetchUser();
}, [fetchUser]);

6.Implement a Debounced Hook
function useDebounce(value, delay) {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const timer = setTimeout(() => {
      setDebouncedValue(value);
    }, delay);

    return () => clearTimeout(timer);
  }, [value, delay]);

  return debouncedValue;
}


7.Prevent the Race Condition

useEffect(() => {
  let ignore = false;

  fetch(`/search?q=${query}`)
    .then(res => res.json())
    .then(data => {
      if (!ignore) {
        setResults(data);
      }
    });
  return () => {
    ignore = true;
  };
}, [query]);

8."Index as Key" Bug

const [todos, setTodos] = useState([
  { id: 1, text: "Walk dog" },
  { id: 2, text: "Buy milk" }
]);

{todos.map(todo => (
  <li key={todo.id}>
    <input defaultValue={todo.text} />
    <button onClick={() => removeTodo(todo.id)}>Delete</button>
  </li>
))}

9.Component Optimization

const items = useMemo(() => [{ id: 1, name: "A" }], []);

10.Dependent Fetches

async function getPostWithAuthor(postId) {
  const postRes = await fetch(`/posts/${postId}`);
  const post = await postRes.json();
  const userRes = await fetch(`/users/${post.authorId}`);
  const user = await userRes.json();
  return {
    ...post,
    author: user
  };
}


