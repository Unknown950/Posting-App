<html>
<head><title>steem-js posting example</title></head>
<body>
<h2>Steemit de bir yaz&#305;y&#305 yaz!</h2>
&Uumlye ad&#305: <input id="username" type="text"><br/>
&#350ifre (Private Posting key): <input id="postingKey" type="password" size="65"><br/>
Ba&#351l&#305;k: <input id="title" type="text"><br/>
Yaz&#305:<br/>
<textarea id="article"></textarea><br/>
<input id="postIt" type="button" value="G&ouml;nder!" onClick=postArticle()>
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
