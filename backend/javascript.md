const person = {
firstName: "Asabeneh",
lastName: "Yetayeh",
age: 250,
country: "Finland",
job: "Instructor and Developer",
skills: [
{HTML:[{hello:["hello1"]},"steve"]},
"CSS",
"JavaScript",
"React",
"Redux",
"Node",
"MongoDB",
"Python",
"D3.js",
],
languages: ["Amharic", "English", "Suomi(Finnish)"],
};
const getPersonInfo = (obj) => {
const skills = obj.skills[1];
const formattedSkills = skills.slice(0, -1).join(", ");
const languages = obj.languages;
const formattedLanguages = languages.slice(0, -1).join(",");

personInfo = `${obj.firstName} ${obj.lastName} lives in ${ obj.country }. He is ${obj.age} years old. He is an ${ obj.job }. He teaches ${formattedSkills} and ${ skills[skills.length - 1] }. He speaks ${formattedLanguages} and a little bit of ${languages[2]}.`;
}

console.log(getPersonInfo(person));
