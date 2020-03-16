-- phpMyAdmin SQL Dump
-- version 4.8.4
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Generation Time: Mar 16, 2020 at 08:23 PM
-- Server version: 10.1.37-MariaDB
-- PHP Version: 7.3.1

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
SET AUTOCOMMIT = 0;
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Database: `schoolmgmt`
--

-- --------------------------------------------------------

--
-- Table structure for table `classe`
--

CREATE TABLE `classe` (
  `id` int(11) NOT NULL,
  `libelle` varchar(255) COLLATE utf8_roman_ci NOT NULL,
  `section` varchar(255) COLLATE utf8_roman_ci NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_roman_ci;

--
-- Dumping data for table `classe`
--

INSERT INTO `classe` (`id`, `libelle`, `section`) VALUES
(1, 'seconde', '');

-- --------------------------------------------------------

--
-- Table structure for table `eleve`
--

CREATE TABLE `eleve` (
  `id` int(11) NOT NULL,
  `nom` varchar(255) COLLATE utf8_roman_ci NOT NULL,
  `parent` varchar(255) COLLATE utf8_roman_ci NOT NULL,
  `date` date NOT NULL,
  `sexe` varchar(10) COLLATE utf8_roman_ci NOT NULL,
  `telephone` varchar(11) COLLATE utf8_roman_ci NOT NULL,
  `classe` varchar(225) COLLATE utf8_roman_ci DEFAULT NULL,
  `section` varchar(255) COLLATE utf8_roman_ci NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_roman_ci;

--
-- Dumping data for table `eleve`
--

INSERT INTO `eleve` (`id`, `nom`, `parent`, `date`, `sexe`, `telephone`, `classe`, `section`) VALUES
(5, 'kkk', 'ip', '2020-03-12', 'Masculin', '9999', '1', '3'),
(6, 'qweqw', 'ip', '2020-03-12', 'Masculin', '9999', '1', '3'),
(7, 'qweqw', 'ip', '2020-03-12', 'Masculin', '9999', '1', '3'),
(8, 'qwd', 'ip', '2020-03-12', 'Masculin', '9999', '1', '3'),
(9, 'aaa', 'ip', '1970-01-01', 'Masculin', '9999', '1', '3'),
(10, 'qws', 'ip', '1970-01-01', 'Masculin', '9999', '1', '3'),
(11, 'uui', 'kljkl', '2020-03-05', 'Masculin', 'mlm', 'seconde', 'lycee');

-- --------------------------------------------------------

--
-- Table structure for table `evaluation`
--

CREATE TABLE `evaluation` (
  `id` int(11) NOT NULL,
  `date` date NOT NULL,
  `classe` int(11) NOT NULL,
  `matiere` int(11) NOT NULL,
  `trimestre` varchar(255) COLLATE utf8_roman_ci NOT NULL,
  `examname` varchar(255) COLLATE utf8_roman_ci NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_roman_ci;

-- --------------------------------------------------------

--
-- Table structure for table `matiere`
--

CREATE TABLE `matiere` (
  `id` int(11) NOT NULL,
  `nomMatiere` varchar(255) COLLATE utf8_roman_ci NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_roman_ci;

--
-- Dumping data for table `matiere`
--

INSERT INTO `matiere` (`id`, `nomMatiere`) VALUES
(1, 'math'),
(2, 'xdas');

-- --------------------------------------------------------

--
-- Table structure for table `note`
--

CREATE TABLE `note` (
  `id` int(11) NOT NULL,
  `eleve` varchar(225) COLLATE utf8_roman_ci NOT NULL,
  `classe` varchar(225) COLLATE utf8_roman_ci NOT NULL,
  `matiere` varchar(225) COLLATE utf8_roman_ci NOT NULL,
  `evaluation` varchar(255) COLLATE utf8_roman_ci NOT NULL,
  `valeur` float NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_roman_ci;

--
-- Dumping data for table `note`
--

INSERT INTO `note` (`id`, `eleve`, `classe`, `matiere`, `evaluation`, `valeur`) VALUES
(1, 'aef', '6eme', 'Math', 'fsw', 23),
(2, 'as', '6eme', 'Math', 's', 12),
(3, 'sas', '6eme', 'Math', 'DSA', 12),
(4, 'as', '6eme', 'Math', 'ol', 30);

-- --------------------------------------------------------

--
-- Table structure for table `scolarite`
--

CREATE TABLE `scolarite` (
  `id` int(11) NOT NULL,
  `montant` float NOT NULL,
  `sid` int(11) NOT NULL,
  `cid` int(11) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_roman_ci;

-- --------------------------------------------------------

--
-- Table structure for table `utilisateur`
--

CREATE TABLE `utilisateur` (
  `id` int(11) NOT NULL,
  `nom` varchar(255) COLLATE utf8_roman_ci NOT NULL,
  `telephone` varchar(225) COLLATE utf8_roman_ci NOT NULL,
  `addresse` varchar(255) COLLATE utf8_roman_ci NOT NULL,
  `username` varchar(255) COLLATE utf8_roman_ci NOT NULL,
  `password` varchar(255) COLLATE utf8_roman_ci NOT NULL,
  `useType` varchar(255) COLLATE utf8_roman_ci NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_roman_ci;

--
-- Dumping data for table `utilisateur`
--

INSERT INTO `utilisateur` (`id`, `nom`, `telephone`, `addresse`, `username`, `password`, `useType`) VALUES
(1, 'ali', '99223', 'lome', 'ali', '123', 'Administrateur'),
(2, 'kljk', '3432', 'lk;l', 'k;\'lk', ';lk', 'Administrateur'),
(3, 'eqw', 'jk', 'jkl', 'klj', 'sfa', 'Administrateur');

--
-- Indexes for dumped tables
--

--
-- Indexes for table `classe`
--
ALTER TABLE `classe`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `eleve`
--
ALTER TABLE `eleve`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `evaluation`
--
ALTER TABLE `evaluation`
  ADD PRIMARY KEY (`id`),
  ADD KEY `fk_cev` (`classe`),
  ADD KEY `fk_mev` (`matiere`);

--
-- Indexes for table `matiere`
--
ALTER TABLE `matiere`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `note`
--
ALTER TABLE `note`
  ADD PRIMARY KEY (`id`);

--
-- Indexes for table `scolarite`
--
ALTER TABLE `scolarite`
  ADD PRIMARY KEY (`id`),
  ADD KEY `fk_cid` (`cid`),
  ADD KEY `fk_sid` (`sid`);

--
-- Indexes for table `utilisateur`
--
ALTER TABLE `utilisateur`
  ADD PRIMARY KEY (`id`);

--
-- AUTO_INCREMENT for dumped tables
--

--
-- AUTO_INCREMENT for table `classe`
--
ALTER TABLE `classe`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=2;

--
-- AUTO_INCREMENT for table `eleve`
--
ALTER TABLE `eleve`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=12;

--
-- AUTO_INCREMENT for table `evaluation`
--
ALTER TABLE `evaluation`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `matiere`
--
ALTER TABLE `matiere`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=3;

--
-- AUTO_INCREMENT for table `note`
--
ALTER TABLE `note`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;

--
-- AUTO_INCREMENT for table `scolarite`
--
ALTER TABLE `scolarite`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;

--
-- AUTO_INCREMENT for table `utilisateur`
--
ALTER TABLE `utilisateur`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

--
-- Constraints for dumped tables
--

--
-- Constraints for table `evaluation`
--
ALTER TABLE `evaluation`
  ADD CONSTRAINT `fk_cev` FOREIGN KEY (`classe`) REFERENCES `classe` (`id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `fk_mev` FOREIGN KEY (`matiere`) REFERENCES `matiere` (`id`) ON DELETE CASCADE ON UPDATE CASCADE;

--
-- Constraints for table `scolarite`
--
ALTER TABLE `scolarite`
  ADD CONSTRAINT `fk_cid` FOREIGN KEY (`cid`) REFERENCES `classe` (`id`) ON DELETE CASCADE ON UPDATE CASCADE,
  ADD CONSTRAINT `fk_sid` FOREIGN KEY (`sid`) REFERENCES `eleve` (`id`);
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
