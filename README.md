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


