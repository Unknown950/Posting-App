<html>
<head><title>steem-js posting example</title></head>
<body>
<h2>Posting App!</h2>
Username: <input id="username" type="text"><br/>
Private Posting key: <input id="postingKey" type="password" size="65"><br/>
Title: <input id="title" type="text"><br/>
Post:<br/>
<textarea id="article"></textarea><br/>
<input id="postIt" type="button" value="Senden!" onClick=postArticle>
</body>
</html>

<script src="https://cdn.steemjs.com/lib/latest/steem.min.js"></script>

<script language="JavaScript">
function postArticle()
{
  steem.broadcast.comment(
    document.getElementById('postingKey').value, // posting wif
    '', // author, leave blank for new post
    'tr', // first tag
    document.getElementById('username').value, // username
    'name-of-my-test-article-post', // permlink
    document.getElementById('title').value, // Title
    document.getElementById('article').value, // Body of post
    // json metadata (additional tags, app name, etc)
    { tags: ['steemit'], app: 'steemjs-test!' },
    function (err, result) {
      if (err)
        alert('Failure! ' + err);
      else
        alert('Bravo!');
    }
  );
}
</script>
