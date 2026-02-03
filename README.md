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
function UserProfile({ userId }) {
  const [user, setUser] = useState(null);
  const fetchUser = useCallback(async () => {
    const res = await fetch(`/api/users/${userId}`);
    setUser(await res.json());
  }, [userId]);
  useEffect(() => {
    fetchUser();
  }, [fetchUser]);
  return <div>{user?.name}</div>;
}

