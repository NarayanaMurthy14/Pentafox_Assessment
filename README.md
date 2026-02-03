# Pentafox_Assessment
1.
React &amp; JavaScript Assessment
async function getUsers(userIds) {
  const requests = userIds.map(id =>
    fetch(`/users/${id}`).then(res => res.json())
  );

  return Promise.all(requests);
}
