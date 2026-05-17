import React, { useState, useEffect } from 'react';
import { Menu, X, ExternalLink, Github, Linkedin, Mail, Phone, MapPin, Download, ChevronDown, Code, Database, Zap, Award, Send } from 'lucide-react';
import { motion, AnimatePresence } from 'framer-motion';

const Portfolio = () => {
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [activeSection, setActiveSection] = useState('home');
  const [scrollY, setScrollY] = useState(0);
  const [formData, setFormData] = useState({ name: '', email: '', message: '' });
  const [formStatus, setFormStatus] = useState('idle'); // idle, loading, success, error
  const [formMessage, setFormMessage] = useState('');

  useEffect(() => {
    const handleScroll = () => setScrollY(window.scrollY);
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const handleFormChange = (e) => {
    const { name, value } = e.target;
    setFormData(prev => ({ ...prev, [name]: value }));
  };

  const handleFormSubmit = async (e) => {
    e.preventDefault();
    
    // Validation
    if (!formData.name.trim() || !formData.email.trim() || !formData.message.trim()) {
      setFormStatus('error');
      setFormMessage('Please fill in all fields');
      return;
    }

    // Email validation
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailRegex.test(formData.email)) {
      setFormStatus('error');
      setFormMessage('Please enter a valid email address');
      return;
    }

    setFormStatus('loading');

    try {
      // Using Formspree - no backend needed!
      const response = await fetch('https://formspree.io/f/xwpevwyk', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          name: formData.name,
          email: formData.email,
          message: formData.message,
        }),
      });

      if (response.ok) {
        setFormStatus('success');
        setFormMessage('Message sent successfully! I will get back to you soon.');
        setFormData({ name: '', email: '', message: '' });
        
        // Reset after 3 seconds
        setTimeout(() => {
          setFormStatus('idle');
          setFormMessage('');
        }, 3000);
      } else {
        setFormStatus('error');
        setFormMessage('Failed to send message. Please try again.');
      }
    } catch (error) {
      setFormStatus('error');
      setFormMessage('Error sending message. Please contact me directly at jadhavchaitanya5911@gmail.com');
    }
  };

  const navItems = [
    { id: 'home', label: 'Home' },
    { id: 'about', label: 'About' },
    { id: 'skills', label: 'Skills' },
    { id: 'projects', label: 'Projects' },
    { id: 'experience', label: 'Experience' },
    { id: 'contact', label: 'Contact' }
  ];

  const projects = [
    {
      id: 1,
      title: 'AI Sales Forecast Dashboard',
      description: 'Power BI dashboard for sales analysis and trend forecasting with KPI tracking',
      tech: ['Power BI', 'DAX', 'Time-Series Analysis'],
      achievements: ['Enabled data-driven decisions', 'Real-time KPI tracking', 'Sales predictions'],
      github: 'https://github.com/chaitanya5711',
      color: 'from-blue-500 to-cyan-500'
    },
    {
      id: 2,
      title: 'AI Resume Analyzer & Feedback System',
      description: 'LLM-powered HR tool analyzing resumes with AI-generated feedback and skill gap analysis',
      tech: ['Streamlit', 'OpenRouter API', 'Prompt Engineering', 'Python'],
      achievements: ['Multi-format support (PDF/DOCX)', 'Skill gap analysis', 'Secure API management'],
      github: 'https://github.com/chaitanya5711',
      color: 'from-purple-500 to-pink-500'
    },
    {
      id: 3,
      title: 'Restaurant Automation using AI Agent',
      description: 'AI-powered system with WhatsApp chatbot for order handling and customer interaction',
      tech: ['Python', 'NLP', 'AI Agent', 'WhatsApp API'],
      achievements: ['Automated workflows', 'Reduced manual effort', 'Real-time customer interaction'],
      github: 'https://github.com/chaitanya5711',
      color: 'from-orange-500 to-red-500'
    },
    {
      id: 4,
      title: 'Netflix Data Analysis',
      description: 'EDA on 8,000+ titles to identify genre trends and content distribution patterns',
      tech: ['Python', 'Pandas', 'Matplotlib', 'Seaborn'],
      achievements: ['Analyzed 8,000+ titles', 'Genre trend insights', 'Regional production patterns'],
      github: 'https://github.com/chaitanya5711',
      color: 'from-red-500 to-rose-500'
    },
    {
      id: 5,
      title: 'Sales and Customer Data Analysis using SQL',
      description: 'SQL-based analysis on sales and customer datasets with complex joins and aggregations',
      tech: ['SQL', 'MySQL', 'Data Analysis', 'Reporting'],
      achievements: ['Complex query optimization', 'Customer behavior insights', 'Revenue analysis'],
      github: 'https://github.com/chaitanya5711',
      color: 'from-green-500 to-teal-500'
    }
  ];

  const skills = {
    'Programming': ['Python', 'Java'],
    'Data Analysis & ML': ['Machine Learning', 'EDA', 'Statistical Analysis', 'Predictive Modeling', 'Feature Engineering', 'Time Series Forecasting', 'Model Evaluation', 'NLP'],
    'Tools & Libraries': ['NumPy', 'Pandas', 'SciPy', 'Scikit-learn', 'Streamlit', 'Matplotlib', 'Seaborn', 'Power BI', 'Excel'],
    'Advanced Tools': ['OpenRouter API', 'BeautifulSoup', 'PyPDF2', 'FPDF', 'Git', 'Jupyter'],
    'Databases': ['MySQL', 'Firebase'],
    'AI Technologies': ['LLMs', 'RAG', 'Generative AI', 'Prompt Engineering']
  };

  const containerVariants = {
    hidden: { opacity: 0 },
    visible: {
      opacity: 1,
      transition: {
        staggerChildren: 0.1,
        delayChildren: 0.2,
      },
    },
  };

  const itemVariants = {
    hidden: { opacity: 0, y: 20 },
    visible: {
      opacity: 1,
      y: 0,
      transition: { duration: 0.5, ease: 'easeOut' },
    },
  };

  return (
    <div className="min-h-screen bg-slate-950 text-gray-50 overflow-hidden">
      {/* Background Effects */}
      <div className="fixed inset-0 bg-gradient-to-br from-slate-950 via-slate-900 to-slate-950 pointer-events-none" />
      <div className="fixed top-0 left-1/4 w-96 h-96 bg-cyan-500/10 rounded-full blur-3xl pointer-events-none" />
      <div className="fixed bottom-0 right-1/4 w-96 h-96 bg-purple-500/10 rounded-full blur-3xl pointer-events-none" />

      {/* Navbar */}
      <motion.nav 
        className="fixed top-0 w-full backdrop-blur-md bg-slate-950/80 border-b border-slate-800 z-50"
        initial={{ y: -100 }}
        animate={{ y: 0 }}
        transition={{ duration: 0.5 }}
      >
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex items-center justify-between h-16">
            {/* Logo */}
            <motion.div className="flex items-center space-x-2" whileHover={{ scale: 1.05 }}>
              <div className="w-8 h-8 bg-gradient-to-r from-cyan-500 to-purple-500 rounded-lg flex items-center justify-center">
                <span className="text-white font-bold text-sm">CJ</span>
              </div>
              <span className="text-lg font-bold bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent">
                Chaitanya Jadhav
              </span>
            </motion.div>

            {/* Desktop Menu */}
            <div className="hidden md:flex items-center space-x-1">
              {navItems.map((item) => (
                <motion.a
                  key={item.id}
                  href={`#${item.id}`}
                  onClick={() => setActiveSection(item.id)}
                  className={`px-4 py-2 rounded-lg transition-all ${
                    activeSection === item.id
                      ? 'text-cyan-400'
                      : 'text-gray-400 hover:text-gray-200'
                  }`}
                  whileHover={{ y: -2 }}
                >
                  {item.label}
                </motion.a>
              ))}
            </div>

            {/* Mobile Menu Button */}
            <button
              onClick={() => setIsMenuOpen(!isMenuOpen)}
              className="md:hidden p-2 rounded-lg hover:bg-slate-800 transition"
            >
              {isMenuOpen ? <X size={24} /> : <Menu size={24} />}
            </button>
          </div>

          {/* Mobile Menu */}
          <AnimatePresence>
            {isMenuOpen && (
              <motion.div
                initial={{ opacity: 0, height: 0 }}
                animate={{ opacity: 1, height: 'auto' }}
                exit={{ opacity: 0, height: 0 }}
                className="md:hidden pb-4 space-y-2"
              >
                {navItems.map((item) => (
                  <a
                    key={item.id}
                    href={`#${item.id}`}
                    onClick={() => {
                      setActiveSection(item.id);
                      setIsMenuOpen(false);
                    }}
                    className="block px-4 py-2 rounded-lg text-gray-400 hover:text-cyan-400 hover:bg-slate-800 transition"
                  >
                    {item.label}
                  </a>
                ))}
              </motion.div>
            )}
          </AnimatePresence>
        </div>
      </motion.nav>

      {/* Hero Section */}
      <section id="home" className="min-h-screen flex items-center justify-center pt-20 px-4 relative">
        <motion.div
          className="max-w-4xl mx-auto text-center z-10"
          variants={containerVariants}
          initial="hidden"
          whileInView="visible"
          viewport={{ once: true }}
        >
          {/* Profile Image Placeholder */}
          <motion.div
            className="mb-8 flex justify-center"
            variants={itemVariants}
          >
            <div className="w-32 h-32 rounded-full bg-gradient-to-br from-cyan-500 to-purple-500 p-1">
              <div className="w-full h-full rounded-full bg-slate-950 flex items-center justify-center text-4xl font-bold">
                CJ
              </div>
            </div>
          </motion.div>

          <motion.h1
            className="text-5xl md:text-7xl font-bold mb-6 bg-gradient-to-r from-cyan-400 via-purple-400 to-pink-400 bg-clip-text text-transparent"
            variants={itemVariants}
          >
            Data Analyst & AI Enthusiast
          </motion.h1>

          <motion.p className="text-xl md:text-2xl text-gray-300 mb-8 leading-relaxed" variants={itemVariants}>
            Results-driven Data Science & AI student with expertise in <span className="text-cyan-400 font-semibold">Python, SQL, Power BI, Machine Learning, and AI applications.</span> Passionate about solving business problems using data-driven insights.
          </motion.p>

          <motion.div className="flex flex-col sm:flex-row gap-4 justify-center mb-12" variants={itemVariants}>
            <motion.a
              href="#projects"
              whileHover={{ scale: 1.05 }}
              whileTap={{ scale: 0.95 }}
              className="px-8 py-3 bg-gradient-to-r from-cyan-500 to-blue-500 rounded-lg font-semibold hover:shadow-lg hover:shadow-cyan-500/50 transition"
            >
              View Projects
            </motion.a>
            <motion.a
              href="https://drive.google.com"
              whileHover={{ scale: 1.05 }}
              whileTap={{ scale: 0.95 }}
              className="px-8 py-3 border-2 border-purple-500 text-purple-400 rounded-lg font-semibold hover:bg-purple-500/10 transition flex items-center justify-center gap-2"
            >
              <Download size={20} /> Download Resume
            </motion.a>
            <motion.a
              href="#contact"
              whileHover={{ scale: 1.05 }}
              whileTap={{ scale: 0.95 }}
              className="px-8 py-3 border-2 border-gray-600 text-gray-300 rounded-lg font-semibold hover:border-gray-400 hover:text-gray-100 transition"
            >
              Contact Me
            </motion.a>
          </motion.div>

          {/* Scroll Indicator */}
          <motion.div
            className="flex justify-center"
            animate={{ y: [0, 10, 0] }}
            transition={{ duration: 2, repeat: Infinity }}
          >
            <ChevronDown className="text-cyan-400" size={32} />
          </motion.div>
        </motion.div>
      </section>

      {/* About Section */}
      <section id="about" className="py-20 px-4 relative">
        <div className="max-w-6xl mx-auto">
          <motion.h2
            className="text-4xl font-bold mb-12 text-center bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent"
            variants={itemVariants}
            initial="hidden"
            whileInView="visible"
            viewport={{ once: true }}
          >
            About Me
          </motion.h2>

          <div className="grid md:grid-cols-2 gap-8">
            <motion.div
              className="bg-slate-900/50 backdrop-blur border border-slate-800 rounded-lg p-8"
              variants={itemVariants}
              initial="hidden"
              whileInView="visible"
              viewport={{ once: true }}
            >
              <h3 className="text-2xl font-bold mb-4 text-cyan-400">Academic Excellence</h3>
              <p className="text-gray-300 mb-4">
                Final-year B.E Information Technology student at <span className="font-semibold text-gray-100">Shrimati Kashibai Navale College of Engineering</span>, Pune (2022-2026).
              </p>
              <p className="text-gray-300 mb-4">
                <span className="font-semibold text-cyan-400">CGPA: 8.08/10</span>
              </p>
              <p className="text-gray-300">
                Strong foundation in Data Analysis, Machine Learning, AI, and Exploratory Data Analysis (EDA). Passionate about solving real-world business problems using data science and AI applications.
              </p>
            </motion.div>

            <motion.div
              className="bg-slate-900/50 backdrop-blur border border-slate-800 rounded-lg p-8"
              variants={itemVariants}
              initial="hidden"
              whileInView="visible"
              viewport={{ once: true }}
            >
              <h3 className="text-2xl font-bold mb-4 text-purple-400">Professional Interests</h3>
              <div className="space-y-3 text-gray-300">
                <p className="flex items-start gap-3">
                  <span className="text-purple-400 mt-1">●</span>
                  <span>Expertise in <span className="font-semibold">LLMs, RAG architectures</span>, and Generative AI applications</span>
                </p>
                <p className="flex items-start gap-3">
                  <span className="text-purple-400 mt-1">●</span>
                  <span>Building <span className="font-semibold">AI-powered solutions</span> that drive business value</span>
                </p>
                <p className="flex items-start gap-3">
                  <span className="text-purple-400 mt-1">●</span>
                  <span>Data visualization and <span className="font-semibold">dashboard development</span> for stakeholder insights</span>
                </p>
                <p className="flex items-start gap-3">
                  <span className="text-purple-400 mt-1">●</span>
                  <span>End-to-end ML pipeline development and <span className="font-semibold">predictive modeling</span></span>
                </p>
              </div>
            </motion.div>
          </div>

          {/* Stats */}
          <motion.div
            className="grid grid-cols-2 md:grid-cols-4 gap-4 mt-12"
            variants={containerVariants}
            initial="hidden"
            whileInView="visible"
            viewport={{ once: true }}
          >
            {[
              { label: 'Projects Completed', value: '5+' },
              { label: 'Technologies', value: '20+' },
              { label: 'Certifications', value: '3' },
              { label: 'Internship Months', value: '6' }
            ].map((stat, idx) => (
              <motion.div
                key={idx}
                className="bg-gradient-to-br from-slate-800/50 to-slate-900/50 border border-slate-700 rounded-lg p-6 text-center"
                variants={itemVariants}
              >
                <p className="text-3xl font-bold bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent">
                  {stat.value}
                </p>
                <p className="text-sm text-gray-400 mt-2">{stat.label}</p>
              </motion.div>
            ))}
          </motion.div>
        </div>
      </section>

      {/* Skills Section */}
      <section id="skills" className="py-20 px-4 relative">
        <div className="max-w-6xl mx-auto">
          <motion.h2
            className="text-4xl font-bold mb-12 text-center bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent"
            initial={{ opacity: 0, y: 20 }}
            whileInView={{ opacity: 1, y: 0 }}
            viewport={{ once: true }}
          >
            Skills & Expertise
          </motion.h2>

          <div className="grid md:grid-cols-2 gap-6">
            {Object.entries(skills).map((category, idx) => (
              <motion.div
                key={idx}
                className="bg-slate-900/50 backdrop-blur border border-slate-800 rounded-lg p-6 hover:border-cyan-500/50 transition"
                variants={itemVariants}
                initial="hidden"
                whileInView="visible"
                viewport={{ once: true }}
                transition={{ delay: idx * 0.1 }}
              >
                <h3 className="text-lg font-bold mb-4 text-cyan-400 flex items-center gap-2">
                  {idx < 2 ? <Code size={20} /> : idx < 4 ? <Zap size={20} /> : <Database size={20} />}
                  {category[0]}
                </h3>
                <div className="flex flex-wrap gap-2">
                  {category[1].map((skill, sidx) => (
                    <motion.span
                      key={sidx}
                      className="px-3 py-1 bg-slate-800 border border-slate-700 rounded-full text-sm text-gray-300 hover:border-purple-500 hover:text-purple-300 transition"
                      whileHover={{ scale: 1.05 }}
                    >
                      {skill}
                    </motion.span>
                  ))}
                </div>
              </motion.div>
            ))}
          </div>
        </div>
      </section>

      {/* Projects Section */}
      <section id="projects" className="py-20 px-4 relative">
        <div className="max-w-6xl mx-auto">
          <motion.h2
            className="text-4xl font-bold mb-12 text-center bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent"
            initial={{ opacity: 0, y: 20 }}
            whileInView={{ opacity: 1, y: 0 }}
            viewport={{ once: true }}
          >
            Featured Projects
          </motion.h2>

          <motion.div
            className="grid md:grid-cols-1 gap-8"
            variants={containerVariants}
            initial="hidden"
            whileInView="visible"
            viewport={{ once: true }}
          >
            {projects.map((project, idx) => (
              <motion.div
                key={project.id}
                className="group bg-slate-900/50 backdrop-blur border border-slate-800 rounded-lg overflow-hidden hover:border-cyan-500/50 transition"
                variants={itemVariants}
              >
                {/* Project Header with Gradient */}
                <div className={`h-2 bg-gradient-to-r ${project.color}`} />

                <div className="p-8">
                  <h3 className="text-2xl font-bold mb-3 text-gray-100 group-hover:text-cyan-300 transition">
                    {project.title}
                  </h3>

                  <p className="text-gray-400 mb-6">{project.description}</p>

                  {/* Tech Stack */}
                  <div className="mb-6">
                    <h4 className="text-sm font-semibold text-gray-300 mb-2 uppercase tracking-wider">Tech Stack</h4>
                    <div className="flex flex-wrap gap-2">
                      {project.tech.map((tech, tidx) => (
                        <span
                          key={tidx}
                          className="px-3 py-1 bg-slate-800 border border-slate-700 rounded-lg text-xs text-gray-300"
                        >
                          {tech}
                        </span>
                      ))}
                    </div>
                  </div>

                  {/* Achievements */}
                  <div className="mb-6">
                    <h4 className="text-sm font-semibold text-gray-300 mb-3 uppercase tracking-wider">Key Achievements</h4>
                    <ul className="space-y-2">
                      {project.achievements.map((achievement, aidx) => (
                        <li key={aidx} className="flex items-start gap-2 text-gray-400 text-sm">
                          <span className="text-cyan-400 mt-1">✓</span>
                          <span>{achievement}</span>
                        </li>
                      ))}
                    </ul>
                  </div>

                  {/* Buttons */}
                  <div className="flex gap-4">
                    <motion.a
                      href={project.github}
                      target="_blank"
                      rel="noopener noreferrer"
                      whileHover={{ scale: 1.05 }}
                      className="flex items-center gap-2 px-4 py-2 bg-slate-800 hover:bg-slate-700 rounded-lg transition text-sm font-semibold text-gray-300"
                    >
                      <Github size={16} /> GitHub
                    </motion.a>
                    <motion.a
                      href="#"
                      whileHover={{ scale: 1.05 }}
                      className="flex items-center gap-2 px-4 py-2 bg-gradient-to-r from-cyan-600 to-blue-600 rounded-lg transition text-sm font-semibold"
                    >
                      <ExternalLink size={16} /> View Live
                    </motion.a>
                  </div>
                </div>
              </motion.div>
            ))}
          </motion.div>
        </div>
      </section>

      {/* Experience Section */}
      <section id="experience" className="py-20 px-4 relative">
        <div className="max-w-6xl mx-auto">
          <motion.h2
            className="text-4xl font-bold mb-12 text-center bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent"
            initial={{ opacity: 0, y: 20 }}
            whileInView={{ opacity: 1, y: 0 }}
            viewport={{ once: true }}
          >
            Experience & Achievements
          </motion.h2>

          <div className="space-y-8">
            {/* Internship */}
            <motion.div
              className="bg-slate-900/50 backdrop-blur border border-slate-800 rounded-lg p-8"
              variants={itemVariants}
              initial="hidden"
              whileInView="visible"
              viewport={{ once: true }}
            >
              <div className="flex items-start justify-between mb-4">
                <div>
                  <h3 className="text-2xl font-bold text-cyan-400">Data Analyst</h3>
                  <p className="text-lg text-gray-400">Maestro Intellect, Pune</p>
                </div>
                <span className="text-sm bg-cyan-500/20 text-cyan-300 px-4 py-2 rounded-full">Nov 2025 - Apr 2026</span>
              </div>
              <ul className="space-y-3 text-gray-300 ml-4">
                <li className="flex items-start gap-3">
                  <span className="text-purple-400 mt-1">→</span>
                  <span>Analyzed and visualized business data using Python, Excel, and Power BI to deliver actionable insights</span>
                </li>
                <li className="flex items-start gap-3">
                  <span className="text-purple-400 mt-1">→</span>
                  <span>Built interactive Power BI dashboards that simplified decision-making for stakeholders</span>
                </li>
                <li className="flex items-start gap-3">
                  <span className="text-purple-400 mt-1">→</span>
                  <span>Cleaned and transformed large datasets using Pandas and NumPy, ensuring data accuracy</span>
                </li>
                <li className="flex items-start gap-3">
                  <span className="text-purple-400 mt-1">→</span>
                  <span>Implemented AI automation to streamline repetitive data tasks, boosting team productivity</span>
                </li>
              </ul>
            </motion.div>

            {/* Certifications */}
            <motion.div
              className="bg-slate-900/50 backdrop-blur border border-slate-800 rounded-lg p-8"
              variants={itemVariants}
              initial="hidden"
              whileInView="visible"
              viewport={{ once: true }}
              transition={{ delay: 0.1 }}
            >
              <h3 className="text-2xl font-bold text-purple-400 mb-6 flex items-center gap-2">
                <Award size={24} /> Certifications & Achievements
              </h3>
              <ul className="space-y-3 text-gray-300">
                <li className="flex items-center gap-3">
                  <span className="text-cyan-400">●</span>
                  <span><span className="font-semibold">Prompt Engineering Frameworks & Methodologies</span> - Advanced AI prompt techniques</span>
                </li>
                <li className="flex items-center gap-3">
                  <span className="text-cyan-400">●</span>
                  <span><span className="font-semibold">Critical Thinking in the AI Era</span> - HP LIFE Training</span>
                </li>
                <li className="flex items-center gap-3">
                  <span className="text-cyan-400">●</span>
                  <span>Participated in <span className="font-semibold">HCL GUVI AI Blogathon 2026</span> - Demonstrated AI and content creation skills</span>
                </li>
              </ul>
            </motion.div>
          </div>
        </div>
      </section>

      {/* Contact Section - WITH WORKING FORM */}
      <section id="contact" className="py-20 px-4 relative">
        <div className="max-w-6xl mx-auto">
          <motion.h2
            className="text-4xl font-bold mb-12 text-center bg-gradient-to-r from-cyan-400 to-purple-400 bg-clip-text text-transparent"
            initial={{ opacity: 0, y: 20 }}
            whileInView={{ opacity: 1, y: 0 }}
            viewport={{ once: true }}
          >
            Get In Touch
          </motion.h2>

          <div className="grid md:grid-cols-2 gap-8">
            {/* Contact Form */}
            <motion.div
              className="bg-slate-900/50 backdrop-blur border border-slate-800 rounded-lg p-8"
              variants={itemVariants}
              initial="hidden"
              whileInView="visible"
              viewport={{ once: true }}
            >
              <h3 className="text-2xl font-bold text-cyan-400 mb-2">Send Me a Message</h3>
              <p className="text-gray-400 mb-6">I'm actively looking for opportunities. Feel free to reach out!</p>

              <form onSubmit={handleFormSubmit} className="space-y-4">
                {/* Name */}
                <motion.div whileHover={{ scale: 1.02 }}>
                  <label className="block text-sm font-semibold text-gray-300 mb-2">Your Name</label>
                  <input
                    type="text"
                    name="name"
                    value={formData.name}
                    onChange={handleFormChange}
                    placeholder="John Doe"
                    className="w-full px-4 py-3 bg-slate-800 border border-slate-700 rounded-lg text-gray-100 placeholder-gray-500 focus:outline-none focus:border-cyan-500 focus:ring-2 focus:ring-cyan-500/20 transition"
                  />
                </motion.div>

                {/* Email */}
                <motion.div whileHover={{ scale: 1.02 }}>
                  <label className="block text-sm font-semibold text-gray-300 mb-2">Your Email</label>
                  <input
                    type="email"
                    name="email"
                    value={formData.email}
                    onChange={handleFormChange}
                    placeholder="john@example.com"
                    className="w-full px-4 py-3 bg-slate-800 border border-slate-700 rounded-lg text-gray-100 placeholder-gray-500 focus:outline-none focus:border-cyan-500 focus:ring-2 focus:ring-cyan-500/20 transition"
                  />
                </motion.div>

                {/* Message */}
                <motion.div whileHover={{ scale: 1.02 }}>
                  <label className="block text-sm font-semibold text-gray-300 mb-2">Message</label>
                  <textarea
                    name="message"
                    value={formData.message}
                    onChange={handleFormChange}
                    placeholder="Tell me about the opportunity or just say hi!"
                    rows="5"
                    className="w-full px-4 py-3 bg-slate-800 border border-slate-700 rounded-lg text-gray-100 placeholder-gray-500 focus:outline-none focus:border-cyan-500 focus:ring-2 focus:ring-cyan-500/20 transition resize-none"
                  />
                </motion.div>

                {/* Status Message */}
                <AnimatePresence>
                  {formMessage && (
                    <motion.div
                      initial={{ opacity: 0, y: -10 }}
                      animate={{ opacity: 1, y: 0 }}
                      exit={{ opacity: 0, y: -10 }}
                      className={`p-3 rounded-lg text-sm font-semibold ${
                        formStatus === 'success'
                          ? 'bg-green-500/20 text-green-300 border border-green-500/50'
                          : 'bg-red-500/20 text-red-300 border border-red-500/50'
                      }`}
                    >
                      {formMessage}
                    </motion.div>
                  )}
                </AnimatePresence>

                {/* Submit Button */}
                <motion.button
                  type="submit"
                  disabled={formStatus === 'loading'}
                  whileHover={{ scale: 1.05 }}
                  whileTap={{ scale: 0.95 }}
                  className={`w-full py-3 rounded-lg font-semibold flex items-center justify-center gap-2 transition ${
                    formStatus === 'loading'
                      ? 'bg-gray-600 cursor-not-allowed'
                      : 'bg-gradient-to-r from-cyan-500 to-blue-500 hover:shadow-lg hover:shadow-cyan-500/50'
                  }`}
                >
                  {formStatus === 'loading' ? (
                    <>
                      <div className="w-4 h-4 border-2 border-gray-300 border-t-white rounded-full animate-spin" />
                      Sending...
                    </>
                  ) : (
                    <>
                      <Send size={18} />
                      Send Message
                    </>
                  )}
                </motion.button>
              </form>
            </motion.div>

            {/* Contact Info */}
            <motion.div
              className="space-y-6"
              variants={containerVariants}
              initial="hidden"
              whileInView="visible"
              viewport={{ once: true }}
            >
              <motion.div
                className="bg-slate-900/50 backdrop-blur border border-slate-800 rounded-lg p-6"
                variants={itemVariants}
              >
                <h3 className="text-lg font-bold text-cyan-300 mb-4">Direct Contact</h3>
                
                <motion.a
                  href="mailto:jadhavchaitanya5911@gmail.com"
                  className="flex items-center gap-4 p-4 bg-slate-800/50 rounded-lg hover:bg-slate-700/50 transition group mb-3"
                  whileHover={{ x: 5 }}
                >
                  <Mail className="text-cyan-400 group-hover:scale-110 transition" size={24} />
                  <div>
                    <p className="text-sm text-gray-400">Email</p>
                    <p className="text-gray-100 font-semibold break-all">jadhavchaitanya5911@gmail.com</p>
                  </div>
                </motion.a>

                <motion.a
                  href="tel:+918767392518"
                  className="flex items-center gap-4 p-4 bg-slate-800/50 rounded-lg hover:bg-slate-700/50 transition group"
                  whileHover={{ x: 5 }}
                >
                  <Phone className="text-purple-400 group-hover:scale-110 transition" size={24} />
                  <div>
                    <p className="text-sm text-gray-400">Phone</p>
                    <p className="text-gray-100 font-semibold">+91-8767392518</p>
                  </div>
                </motion.a>
              </motion.div>

              <motion.div className="bg-gradient-to-br from-cyan-500/20 to-blue-500/20 border border-cyan-500/30 rounded-lg p-6" variants={itemVariants}>
                <h4 className="text-lg font-bold text-cyan-300 mb-2">Connect on Social</h4>
                <div className="flex gap-4">
                  <motion.a
                    href="https://github.com/chaitanya5711"
                    target="_blank"
                    rel="noopener noreferrer"
                    whileHover={{ scale: 1.2 }}
                    className="p-3 bg-slate-800 rounded-lg hover:bg-slate-700 transition"
                  >
                    <Github className="text-gray-300" size={24} />
                  </motion.a>
                  <motion.a
                    href="https://linkedin.com/in/chaitanyatj"
                    target="_blank"
                    rel="noopener noreferrer"
                    whileHover={{ scale: 1.2 }}
                    className="p-3 bg-slate-800 rounded-lg hover:bg-slate-700 transition"
                  >
                    <Linkedin className="text-blue-400" size={24} />
                  </motion.a>
                </div>
              </motion.div>

              <motion.div className="bg-gradient-to-br from-purple-500/20 to-pink-500/20 border border-purple-500/30 rounded-lg p-6" variants={itemVariants}>
                <h4 className="text-lg font-bold text-purple-300 mb-2">Location</h4>
                <div className="flex items-center gap-2 text-gray-300">
                  <MapPin className="text-red-400" size={20} />
                  <span>Pune, Maharashtra, India</span>
                </div>
              </motion.div>

              <motion.div className="bg-gradient-to-br from-orange-500/20 to-red-500/20 border border-orange-500/30 rounded-lg p-6" variants={itemVariants}>
                <h4 className="text-lg font-bold text-orange-300 mb-2">Currently Available</h4>
                <p className="text-gray-300 text-sm">Open to Data Analyst, AI/ML Intern, and Data Science roles in Pune & NCR region.</p>
              </motion.div>
            </motion.div>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="border-t border-slate-800 bg-slate-950/50 py-12 px-4">
        <div className="max-w-6xl mx-auto">
          <div className="grid md:grid-cols-3 gap-8 mb-8">
            <div>
              <h4 className="font-bold text-gray-100 mb-4">Quick Links</h4>
              <ul className="space-y-2 text-gray-400 text-sm">
                <li><a href="#home" className="hover:text-cyan-400 transition">Home</a></li>
                <li><a href="#projects" className="hover:text-cyan-400 transition">Projects</a></li>
                <li><a href="#contact" className="hover:text-cyan-400 transition">Contact</a></li>
              </ul>
            </div>
            <div>
              <h4 className="font-bold text-gray-100 mb-4">Connect</h4>
              <div className="flex gap-4">
                <motion.a href="https://github.com/chaitanya5711" target="_blank" rel="noopener noreferrer" whileHover={{ scale: 1.2 }}>
                  <Github className="text-gray-400 hover:text-cyan-400 transition" size={20} />
                </motion.a>
                <motion.a href="https://linkedin.com/in/chaitanyatj" target="_blank" rel="noopener noreferrer" whileHover={{ scale: 1.2 }}>
                  <Linkedin className="text-gray-400 hover:text-blue-400 transition" size={20} />
                </motion.a>
                <motion.a href="mailto:jadhavchaitanya5911@gmail.com" whileHover={{ scale: 1.2 }}>
                  <Mail className="text-gray-400 hover:text-purple-400 transition" size={20} />
                </motion.a>
              </div>
            </div>
            <div>
              <h4 className="font-bold text-gray-100 mb-4">Status</h4>
              <p className="text-gray-400 text-sm">🟢 Open to opportunities in Data & AI roles</p>
            </div>
          </div>

          <div className="border-t border-slate-800 pt-8 flex flex-col sm:flex-row justify-between items-center text-gray-400 text-sm">
            <p>&copy; 2026 Chaitanya Jadhav. All rights reserved.</p>
            <p>Built with <span className="text-red-500">❤</span> using React, Tailwind & Framer Motion</p>
          </div>
        </div>
      </footer>
    </div>
  );
};

export default Portfolio;
