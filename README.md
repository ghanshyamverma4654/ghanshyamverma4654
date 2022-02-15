### Hola, I'm Ghanshyam Verma! 👋

- 🔭 I’m currently working on, Web Development: "Our Coaching".
- 🌱 I’m currently learning SQL, Operating System & Computer Networks.
- 👯 I’m looking to collaborate on Flutter Development.
- 🤔 I’m looking for help with https://www.sanfoundry.com/ & https://flutter.dev/.
- 💬 Ask me about - Java And Web Development.
- 📫 How to reach me: LinkedIn: https://www.linkedin.com/in/ghanshyam-verma-480426203/
- :email:             Email-Id: ghanshyam.verma_cs19@gla.ac.in
- 😄 Pronouns: He/His
- ⚡ Fun fact: I spend almost 12 hours listening songs everday.

<!-- -![gitImages](https://user-images.githubusercontent.com/67820202/112162579-3156bc80-8c12-11eb-97b6-2195cb0ca94d.jpg) -->
<!-- <h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://www.cprogramming.com/" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/c/c-original.svg" alt="c" width="40" height="40"/> </a> <a href="https://dart.dev" target="_blank"> <img src="https://www.vectorlogo.zone/logos/dartlang/dartlang-icon.svg" alt="dart" width="40" height="40"/> </a> <a href="https://flutter.dev" target="_blank"> <img src="https://www.vectorlogo.zone/logos/flutterio/flutterio-icon.svg" alt="flutter" width="40" height="40"/> </a> <a href="https://www.java.com" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="java" width="40" height="40"/> </a> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="javascript" width="40" height="40"/> </a> <a href="https://www.linux.org/" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" alt="linux" width="40" height="40"/> </a> <a href="https://www.mysql.com/" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/> </a> <a href="https://www.python.org" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a> </p> -->

[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=ghanshyamverma4654&layout=compact)](https://github.com/ghanhshyamverma4654/github-readme-stats)

![Ghanshyam Verma GitHub stats](https://github-readme-stats.vercel.app/api?username=ghanshyamverma4654&show_icons=true&theme=radical)


function normalcdf(mean, sigma, to) {
  var z = (to - mean) / Math.sqrt(2 * sigma * sigma);
  var t = 1 / (1 + 0.3275911 * Math.abs(z));
  var a1 = 0.254829592;
  var a2 = -0.284496736;
  var a3 = 1.421413741;
  var a4 = -1.453152027;
  var a5 = 1.061405429;
  var erf =
    1 - ((((a5 * t + a4) * t + a3) * t + a2) * t + a1) * t * Math.exp(-z * z);
  var sign = 1;
  if (z < 0) {
    sign = -1;
  }
  return (1 / 2) * (1 + sign * erf);
}

function calculateRank({
  totalRepos,
  totalCommits,
  contributions,
  followers,
  prs,
  issues,
  stargazers,
}) {
  const COMMITS_OFFSET = 1.65;
  const CONTRIBS_OFFSET = 1.65;
  const ISSUES_OFFSET = 1;
  const STARS_OFFSET = 0.75;
  const PRS_OFFSET = 0.5;
  const FOLLOWERS_OFFSET = 0.45;
  const REPO_OFFSET = 1;

  const ALL_OFFSETS =
    CONTRIBS_OFFSET +
    ISSUES_OFFSET +
    STARS_OFFSET +
    PRS_OFFSET +
    FOLLOWERS_OFFSET +
    REPO_OFFSET;

  const RANK_S_VALUE = 1;
  const RANK_DOUBLE_A_VALUE = 25;
  const RANK_A2_VALUE = 45;
  const RANK_A3_VALUE = 60;
  const RANK_B_VALUE = 100;

  const TOTAL_VALUES =
    RANK_S_VALUE + RANK_A2_VALUE + RANK_A3_VALUE + RANK_B_VALUE;

  // prettier-ignore
  const score = (
    totalCommits * COMMITS_OFFSET +
    contributions * CONTRIBS_OFFSET +
    issues * ISSUES_OFFSET +
    stargazers * STARS_OFFSET +
    prs * PRS_OFFSET +
    followers * FOLLOWERS_OFFSET + 
    totalRepos * REPO_OFFSET 
  ) / 100;

  const normalizedScore = normalcdf(score, TOTAL_VALUES, ALL_OFFSETS) * 100;

  let level = "";

  if (normalizedScore < RANK_S_VALUE) {
    level = "S+";
  }
  if (
    normalizedScore >= RANK_S_VALUE &&
    normalizedScore < RANK_DOUBLE_A_VALUE
  ) {
    level = "S";
  }
  if (
    normalizedScore >= RANK_DOUBLE_A_VALUE &&
    normalizedScore < RANK_A2_VALUE
  ) {
    level = "A++";
  }
  if (normalizedScore >= RANK_A2_VALUE && normalizedScore < RANK_A3_VALUE) {
    level = "A+";
  }
  if (normalizedScore >= RANK_A3_VALUE && normalizedScore < RANK_B_VALUE) {
    level = "B+";
  }

  return { level, score: normalizedScore };
}

module.exports = calculateRank;
